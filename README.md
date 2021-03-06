# cmrf

Participating in [MSR-Bing Image Retrieval Challenge](http://research.microsoft.com/en-US/projects/irc/), 
we proposed **C**ross-**M**edia **R**elevance **F**usion[1].
The **cmrf** package completely implements Cross-Media Relevance Fusion, with
* four individual methods (i.e. image2text, text2image, text2image as Parzen window and semantic embedding),
* learning optimized weights for relevance fusion,
* cross-platform support (linux, mac, windows).


### Dependency:
* Download [data](http://www.mmc.ruc.edu.cn/research/irc2015/data/rucmmc_irc2015_data.tar.gz) without image visual feature.
* Download image visual feature [ [required](http://www.mmc.ruc.edu.cn/research/irc2015/data/rucmmc_irc2015_required_feature.tar.gz)| [optional](http://www.mmc.ruc.edu.cn/research/irc2015/data/rucmmc_irc2015_optional_feature.tar.gz)]
* Add [simpleknn](simpleknn) to `PYTHONPATH`.
* Change `ROOT_PATH` in [basic/common.py](basic/common.py) to local folder where data are stored in.



### Description:
In order to generate cross-media relevance, image and query have to be represented in a common space as they are of two distinct modalities. In our package, we implement four individual methods for cross-media relevance computation and a late-fusion method for cross-media relevance fusion.

#####Individual methods:
* [image2text](image2text.py): project image into Bag-of-Words space.
* [text2image](text2image.py): project query into visual feature space.
* [text2image as Parzen window](parzenWindow.py): an extreme case of text2image.
* [semantic embedding](semantic_embedding.py):  project image and query into a learned semantic space.

#####Relevance fusion:
* [weight optimization](weightOptimization.py): employ Coordinate Ascent to learn optimized weights
* [relevance fusion](relevanceFusion.py): fuse relevance from different methods with optimized weights.


### Get Started:
You can run [doit.sh](doit.sh) to see if everything in place.
If it run successfully, the cross-media relevance of all the query-imge pairs will be written in `result/final.result.txt` folder, and other intermediate results will also appear in `result` folder.


### Note:
* As a show case, we only run 20 queries. If you want to run all the 1000 queries from Dev set, please rename  'qid.text.all.txt' in `/rootpath/msr2013dev/Annotations/` to 'qid.text.txt'. It will take a while.
* If you would like to use your own dataset, we recommand you to organize dataset in a fixed structure like our data, which can minimize your coding effort.
* The package does not include any visual feature extractors. Features of data need to be pre-computed, and converted to required binary format using [txt2bin.py](simpleknn/txt2bin.py).


### Reference:

[1] Jianfeng Dong, Xirong Li, Shuai Liao, Jieping Xu, Duanqing Xu, Xiaoyong Du. [Image Retrieval by Cross-Media Relevance Fusion](http://www.mmc.ruc.edu.cn/research/irc2015/p173-dong.pdf). ACM Multimedia 2015 (Grand Challenge Session)
