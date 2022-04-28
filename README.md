### Training MaskRCNN for Segmentation Task from the Scrach

This script is for training the a MaskRCNN-Semantic-Segmentation model using COCO dataset. 

Reference: [Mask R-CNN for Object Detection and Segmentation](https://github.com/matterport/Mask_RCNN)

DL framework is:
- Tensorflow ver 1 (Tensorflow-GPU==1.15.0)
- Python = 3.6

### 1 - Setup
- Clone the repo, setup the virtual env
```angular2html

git clone https://github.com/matterport/Mask_RCNN.git
cd Mask_RCNN

mkdir P36
virtualenv -p python3.6 P36
source P36/bin/activate

pip3 install -r requirements.txt

# however, the default requirements.txt may lead to some problems
pip uninstall -y tensorflow
pip install h5py==2.10.0
pip install tensorflow==1.15
pip install tensorflow-gpu==1.15.0
pip install keras==2.1.6

python3 setup.py install
```

### 2 - Prepare the COCO dataset. 

Install a toolkit for COCO dataset pre-process: 
```angular2html
pip install "git+https://github.com/philferriere/cocoapi.git#egg=pycocotools&subdirectory=PythonAPI"
```

We have COCO dataset at multiple locations. I am using the one at `/nfs_1/data/coco`. This script use label `2014` as default. 

### 3 - Download pretrained model and Train

Reference at https://github.com/matterport/Mask_RCNN/releases

Example: I pick up the original COCO pretrained model: `mask_rcnn_coco.h5`.
```angular2html
# from Mask_RCNN/
mkdir pretrain
cd pretrain
wget https://github.com/matterport/Mask_RCNN/releases/download/v2.0/mask_rcnn_coco.h5
```

The training flags are as followings:
```angular2html
# from directory "models/research/"
python samples/coco/coco.py train --dataset=/nfs_1/data/coco --model=pretrain/mask_rcnn_coco.h5
```
