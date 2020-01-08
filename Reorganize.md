针对pytorch-1.0分支的一些建议
-------------------------------------------------------------------------------------------------------------------
# 步骤

1.下载pytorch1.0分支

git clone https://github.com/jwyang/faster-rcnn.pytorch.git -b pytorch-1.0

2.下载cocoAPI

git clone https://github.com/xiaolonghao/cocoapi.git

3.进入主目录并创建dada文件夹

cd faster-rcnn.pytorch && mkdir data

注：创建数据库时用

datadir=`echo $PWD`

4. 安装库文件

注意：要求python=3.6.5 pytorch=1.0.0  torchvision=0.2.1 pillow=6.2.1 scipy=1.4.1等（亲测可以，别的需要自己测试）

pip install -r new_requirements.txt

5.升级 gcc为5

conda install -c psi4 gcc-5

6.安装cocoAPI

(1)安装cocoAPI 到 python 的 site-packages 中

cd ../cocoapi/PythonAPI

make install

或者(2) 安装cocoAPI 到pytorch1.0分支中

mv pycocotools/ ../../faster-rcnn.pytorch/lib

7.编译

python setup.py build develop

-----------------------------------------------------------------------------------------------------------------


# 如果没有数据库可以通过以下步骤下载数据库

1. 下载链接

git clone https://github.com/xiaolonghao/detection_datas_url.git

2. 解压并进入对应文件夹运行download.sh

tar -xf -xvf detection_datas_url/detection_datas.tar.gz

例如voc2007：

cd detection_datas/voc2007/

sh download.sh

tar -xf VOCtrainval_06-Nov-2007.tar

tar -xf VOCtest_06-Nov-2007.tar

tar -xf VOCdevkit_08-Jun-2007.tar

ln -s VOCdevkit  $datadir/VOCdevkit2007

cd -

例如voc2012：

cd detection_datas/voc2012/

sh download.sh

tar -xf VOCtrainval_11-May-2012.tar

ln -s VOCdevkit  $datadir/VOCdevkit2012

cd -

例如coco2014：

cd detection_datas/coco2014/

sh download.sh

...
...

cd -

例如coco2017：

cd detection_datas/coco2017/

sh download.sh

...
...

cd -

