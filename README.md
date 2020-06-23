# [Spatially Variant Linear Representation Models for Joint Filtering](http://openaccess.thecvf.com/content_CVPR_2019/papers/Pan_Spatially_Variant_Linear_Representation_Models_for_Joint_Filtering_CVPR_2019_paper.pdf)

## Dependencies

- Python = 3.8
- PyTorch = 1.5
- TensorBoard
- numpy
- os
- cv2
- PIL
- glob
- logging

## Training
I trained and tested the model on a single NVIDIA RTX 2080Ti GPU, and this process took about 9 hours for 50w iterations. The training strategies are the same as paper.

- Command

```bash
#x4
python train.py --upscaling_factor 4 --crop
#x8
python train.py --upscaling_factor 8 --crop
#x16
python train.py --upscaling_factor 16 --crop
```

## Testing

```bash
#x4
python test.py --upscaling_factor 4 --model weights/X4/model_10000_epoch.pth
#x8
python test.py --upscaling_factor 8 --model weights/X8/model_10000_epoch.pth
#x16
python test.py --upscaling_factor 16 --model weights/X16/model_10000_epoch.pth
```

## Results

- Quantitative results (RMSE)

| Depth Image SR | SVLRM (paper) | 5×10^5 iterations | 9×10^4 iterations |
| :----- | :-----: | :-----: | :-----: |
| x4 | 1.74 | 1.66738 | 1.8039 |
| x8 | 5.59 | 3.20587 | 3.3889 |
| x16 | 7.23 | 5.82709 | 6.0919 |

Our all models results can download from [Baidu Cloud](https://pan.baidu.com/s/17Myh_xhocOFs7sgzqNvhUA)  code: drkb or [Google Drive](https://drive.google.com/drive/folders/17ADNrYqn7Fj0IhuefBxSKcaKyHrfJan0?usp=sharing)


- Visual results (X8 depth sr)

on the left is output of the model, on the right is the corresponding ground truth image
<img src="./results/X8/065.png" width="400"/> <img src="./results/gt/001065.png" width="400"/>

img_001065 || RMSE:2.7260 || PSNR:39.4204 || SSIM:0.9820

<img src="./results/X8/101.png" width="400"/> <img src="./results/gt/001101.png" width="400"/>

img_001101 || RMSE:3.9308 || PSNR:36.2413 || SSIM:0.9749

<img src="./results/X8/215.png" width="400"/> <img src="./results/gt/001215.png" width="400"/>

img_001215  || RMSE:2.7663 || PSNR:39.2927 || SSIM:0.9838

<img src="./results/X8/320.png" width="400"/> <img src="./results/gt/001320.png" width="400"/>

img_001320 || RMSE:3.8851 || PSNR:36.3428 || SSIM:0.9762

<img src="./results/X8/436.png" width="400"/> <img src="./results/gt/001436.png" width="400"/>

img_001436 || RMSE:3.4263 || PSNR:37.4344 || SSIM:0.9871
## Acknowledgements
- [SVLRM_matlab](https://www.dropbox.com/s/1z9ps20welw3c9a/CVPR19_SV_code.zip?dl=0)
- [SVLRM_Pytorch](https://github.com/curlyqian/SVLRM)
