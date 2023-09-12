# AICAM
The official code for AICAM
Our code will be published soon.
![image](https://github.com/diaodiao317/AICAM/blob/main/vis.png)

## Performance
| Method      | Seed Mask           | Pseudo mask | Seg result(val) | Seg result(test) | Weight/logs |
|-------------|---------------------|-------------|-----------------|------------------|-------------|
| AICAM       | 55.1(54.9 in paper) | 71.0        | 68.6            | 68.5             |[drive](https://drive.google.com/drive/folders/1LFajOCDcERd1mUUHmlLtG1KM4Fw6URPN?usp=sharing)             |
| AICAM†      | 55.1(54.9 in paper) | 71.0        | 70.6            | 70.8             |[drive](https://drive.google.com/drive/folders/1LFajOCDcERd1mUUHmlLtG1KM4Fw6URPN?usp=sharing)             |
|  AICAM+AMN† | 66                  | 72.4        | 70.8            | 70.8             |[drive](https://drive.google.com/drive/folders/1c727fHKvToiypuNME4i-2y2KRihYoCkm?usp=sharing)              |
| AICAM+LPCAM | 55.6                | 71.4        | 69.0            | 69.2             |[drive](https://drive.google.com/drive/folders/13nDmNujDuGycrXlKCUpLjgMacSv3MwX4?usp=drive_link)             |


### VOC12


## Prerequisite
- In environment.yml

## Usage 
### Step 1. Prepare dataset.
- Download PASCAL VOC 2012 devkit from [official website](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/#devkit). [Download](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCtrainval_11-May-2012.tar).

### Step 2. Train AICAM and generate seeds.
```
python run_sample.py --voc12_root ../VOCdevkit/VOC2012/ --train_cam_pass True --train_aicam_pass True --make_aicam_pass True --eval_cam_pass True 
```
### Step 3. Train IRN and generate pseudo masks.
```
python run_sample.py --voc12_root ./VOCdevkit/VOC2012/ --cam_to_ir_label_pass True --train_irn_pass True --make_sem_seg_pass True --eval_sem_seg_pass True 
```
### Step 4. Train semantic segmentation network.

Remember to use pseudo masks to replace ground truth. To train DeepLab-v2, we refer to [deeplab-pytorch](https://github.com/kazuto1011/deeplab-pytorch). All hyperparameters use default settings.


## Acknowledgment
This code is borrowed from [IRN](https://github.com/jiwoon-ahn/irn), [ReCAM](https://github.com/zhaozhengChen/ReCAM) and [C2AM](https://github.com/yiping-wang/c2am), thanks!
