# SubterraVision
This is the code of the paper "SubterraVision: A Computational Deep Learning Framework for Low-Light Image Enhancement in Underground Minings"

This is built upon [ZeroDCE](https://github.com/Li-Chongyi/Zero-DCE)

## Setup

1. Create and activate a Python virtual environment:

   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```

2. Upgrade pip and install required packages:

   ```bash
   python -m pip install --upgrade pip
   python -m pip install torch torchvision numpy pillow matplotlib scikit-image pytorch-ssim
   ```

## Training

Run the training script with default settings:

```bash
python lowlight_train.py
```

Optional arguments:

- `--lowlight_images_path`: path to the training images folder (default: `data/train_data/`)
- `--num_epochs`: number of epochs (default: `150`)
- `--train_batch_size`: batch size (default: `8`)
- `--lr`: learning rate (default: `0.0001`)
- `--snapshot_iter`: save a checkpoint every N iterations (default: `10`)
- `--snapshots_folder`: output folder for model checkpoints (default: `snapshots_Zero_DCE++/`)

Example:

```bash
python lowlight_train.py --lowlight_images_path data/train_data/ --num_epochs 150 --train_batch_size 8 --lr 0.0001
```

## Testing

Run the test script with its default settings:

```bash
python lowlight_test.py
```

By default, the script expects test images in `data/test_data/` and loads a pretrained checkpoint from `snapshots_Zero_DCE++/Epoch150.pth`. Adjust the script or checkpoint path if needed.



## Results

The following tables and figures are placeholders from the manuscript. Fill them in with your final values and images.

### Tables

- Table 1: Model performance comparison

  | Metric | Baseline | Proposed | Notes |
  |-------|---------|----------|-------|
  | PSNR  |         |          |       |
  | SSIM  |         |          |       |
  | NIQE  |         |          |       |

- Table 2: Ablation study

  | Component | Description | Result |
  |----------|-------------|--------|
  |          |             |        |
  |          |             |        |

### Figures

- Figure 1: Example input and enhanced output

  ![Figure 1](path/to/figure1.png)

- Figure 2: Qualitative comparison with baseline methods

  ![Figure 2](path/to/figure2.png)

- Figure 3: Training loss curves

  ![Figure 3](path/to/figure3.png)


## If you like this work, then consider citing

```
@article{tiwari2026subterravision,
  title={SubterraVision: A Computational Deep Learning Framework for Low-Light Image Enhancement in Underground Mining},
  author={Tiwari, Naveen Kumar and Bajpai, Abhishek and Singh, Nivedita},
  journal={Engineering Research Express},
  year={2026}
}
```


