### A TensorFlow 2.4  Implementation of MaskRCNN

This script is for training the a MaskRCNN Instance Segmentation model using COCO dataset. The training script is on single GPU with an utilization rate 33%. 

Reference: [Mask R-CNN for Object Detection and Segmentation](https://github.com/matterport/Mask_RCNN)

DL framework is:
- Tensorflow 2.0 (e.g., 2.4.0)
- Python >= 3.4 (e.g., 3.6)
- CUDA >= 11.0, <= 11.4 (e.g., 11.4)

Check the 

### 1 - Setup
- Clone the repo, setup the virtual env
```angular2html

git clone https://github.com/YHDING23/TF2_MASKRCNN.git
cd TF2_MASKRCNN
mkdir venv_TF2
virtualenv -p python3.6 venv_TF2
source venv_TF2/bin/activate

pip install -r requirements.txt
python setup.py install
```

### 2 - Prepare the COCO dataset. 

Install a toolkit for COCO dataset pre-process: 
```angular2html
pip install "git+https://github.com/philferriere/cocoapi.git#egg=pycocotools&subdirectory=PythonAPI"
```

We have COCO dataset at multiple locations. I am using the one at `/nfs_1/data/coco`. This script uses the folders with  label `2014` as default. 

### 3 - Download pretrained model and Train

Reference at https://github.com/matterport/Mask_RCNN/releases

Example: I pick up the original COCO pretrained model: `mask_rcnn_coco.h5`.
```angular2html
# from TF2_MASKRCNN/
mkdir pretrain
cd pretrain
wget https://github.com/matterport/Mask_RCNN/releases/download/v2.0/mask_rcnn_coco.h5
```

The training flags are as followings:
```angular2html
# from TF2_MASKRCNN
python samples/coco/coco.py train --dataset=/nfs_1/data/coco --model=pretrain/mask_rcnn_coco.h5
```
