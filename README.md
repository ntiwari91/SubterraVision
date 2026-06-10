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


## If you like this work, then consider citing

```
@article{tiwari2026subterravision,
  title={SubterraVision: A Computational Deep Learning Framework for Low-Light Image Enhancement in Underground Mining},
  author={Tiwari, Naveen Kumar and Bajpai, Abhishek and Singh, Nivedita},
  journal={Engineering Research Express},
  year={2026}
}
```


