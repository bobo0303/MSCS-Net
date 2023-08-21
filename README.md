# MSCSWT-Net: IMAGE INPAINTING BY MSCSWIN TRANSFORMER ADVERSARIAL AUTOENCODER

Image inpainting has been researched for years. From deeper and larger models to models that focus on global information, all of them aim to obtain results closer to reality. In this paper, we combine the stripe window and line-by-line feature shift to modify the Vision Transformer (ViT) to reduce the computation cost and obtain global information from the oblique attention. In addition, we design a new loss function to enhance the texture and colors for inpainting. At last, to validate
the efficacy of our proposed model, we conduct extensive experiments on commonly seen datasets (Places2 and CelebA) compared with other state-of-the-art methods.
<img src="https://i.imgur.com/fKwnAeL.png" alt="https://i.imgur.com/fKwnAeL.png" title="https://i.imgur.com/fKwnAeL.png" width="1312" height="350">

# Environment
- Python 3.7.0
- pytorch
- opencv
- PIL  
- colorama

or see the requirements.txt

# How to try

## Download dataset (places2、CelebA、ImageNet)
[Places2](http://places2.csail.mit.edu/)  
[CelebA](https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)  
[ImageNet](https://www.image-net.org/download.php)

## Set dataset path

Edit txt/xxx.txt (set path in config)
```python

data_path = './txt/train_path.txt'
mask_path = './txt/train_mask_path.txt'
val_path = './txt/val_path.txt'
val_mask_path = ./txt/val_mask_path.txt'
test_path: './txt/test_path.txt'
test_mask_1_60_path: ./txt/test_mask_1+10.txt'

```

txt example
```python

E:/Places2/data_256/00000001.jpg
E:/Places2/data_256/00000002.jpg
E:/Places2/data_256/00000003.jpg
E:/Places2/data_256/00000004.jpg
E:/Places2/data_256/00000005.jpg
 ⋮

```

## Preprocessing  
In this implementation, masks are automatically generated by ourself. stroke masks mixed randomly to generate proportion from 1% to 60%.

strokes (from left to right 20%-30% 30%-40% 40%-50% 50%-60%)
<img src="https://imgur.com/m3CStkN.png" alt="https://imgur.com/m3CStkN.png" title="https://imgur.com/m3CStkN.png" width="1000" height="200">

## Pretrained model
["Here"](https://drive.google.com/drive/u/4/folders/1QeLZc7_4TZVZ7awRQXNmgvGtPl6OGUAR)

## Run training
```python

python train.py (main setting data_path/mask_path/val_path/val_mask_path/batch_size/train_epoch)

```
1. set the config path ('./config/model_config.yml')
2. Set path and parameter details in model_config.yml

Note: If the training is interrupted and you need to resume training, you can set resume_ckpt and resume_D_ckpt.

## Run testing
```python

python test.py (main setting test_ckpt/test_path/test_mask_1_60_path/save_img_path)

```
1. set the config path ('./config/model_config.yml')
2. Set path and parameter details in model_config.yml

## Quantitative comparison

- Places2 & CelebA

<img src="https://i.imgur.com/7Ey8KfY.png" width="1312" height="350">

Quantitative evaluation of inpainting on Places2 and CelebA datasets. We report Peak signal-to-noise ratio (PSNR), structural similarity (SSIM), Learned Perceptual Image Patch Similarity (LPIPS) and Frechet inception distance ´ (FID) metrics. The ▲ denotes more, and ▼ denotes less of the parameters compared to our proposed model. (Bold means the 1st best; Underline means the 2nd best)

All training and testing base on same 3060.

## Qualitative comparisons

- Places2 & CelebA

<img src="https://i.imgur.com/ouwGw0h.png" width="1000" style="zoom:100%;">

Qualitative results of Places2 dataset among all compared models. From left to right: Masked image, CA, PC, RW, DeepFill-v2, Iconv, AOT-GAN, CRFill, TFill, SWMH-Net, and Ours. Zoom-in for details.

## Ablation study


<div align=center>
<img src="https://i.imgur.com/lKd5Veh.png" width="800" height="250">
</div>

Ablation study table of GC, RDC, MSCSWin Transformer, and HSV loss. We report Peak signal-to-noise ratio (PSNR), structural similarity (SSIM), Learned Perceptual Image Patch Similarity (LPIPS) and Frechet inception distance ´ (FID) metrics.

## Object removal

<div align=center>
<img src="https://i.imgur.com/sG8HJEu.png.jpg" width="1300" height="350">
</div>

Object removal (size 256×256) results. From left to right: Original image, mask, object removal result.

## Acknowledgement
This repository utilizes the codes of following impressive repositories   
- [ZITS](https://github.com/DQiaole/ZITS_inpainting)
- [LaMa](https://github.com/saic-mdal/lama)
- [CSWin Transformer](https://github.com/microsoft/CSWin-Transformer)
- [Vision Transformer](https://github.com/google-research/vision_transformer)
- [SWMHT-Net](https://github.com/bobo0303/LIGHTWEIGHT-IMAGE-INPAINTING-BY-STRIPE-WINDOW-TRANSFORMER-WITH-JOINT-ATTENTION-TO-CNN)

---
## Contact
If you have any question, feel free to contact wiwi61666166@gmail.com
