# SubterraVision
This is the code of the paper "SubterraVision: A Computational Deep Learning Framework for Low-Light Image Enhancement in Underground Minings"

This is built upon [ZeroDCE](https://github.com/Li-Chongyi/Zero-DCE)


## Architecture

<p align="center">
  <img width="1282" alt="DLLNet Architecture"
       src="https://github.com/user-attachments/assets/b2953a87-f424-4201-8b0c-4fae9fb7237f">
  <br><br>
  <b>Figure 1.</b>
  <em>Block diagram of an image enhancement system with local feature extraction and channel self-attention module.</em>
</p>

<br>

<p align="center">
  <img width="761" alt="Channel Module"
       src="https://github.com/user-attachments/assets/5ca6e0a4-20fd-4030-b0df-b7f5412180eb">
  <br><br>
  <b>Figure 2.</b>
  <em>Detailed channel communication workflow.</em>
</p>


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
### Quantitative evaluation

<p align="center">
  <b>Table 1.</b>
  <em>PSNR and SSIM metrics for the SICE Part 2 testing dataset.</em>
</p>

<table align="center">
  <thead>
    <tr>
      <th>S. No.</th>
      <th>Method</th>
      <th>PSNR</th>
      <th>SSIM</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>SRIE</td><td>14.41</td><td>0.54</td></tr>
    <tr><td>2</td><td>LIME</td><td>16.17</td><td>0.57</td></tr>
    <tr><td>3</td><td>Li et al.</td><td>15.19</td><td>0.54</td></tr>
    <tr><td>4</td><td>RetinexNet</td><td>15.99</td><td>0.53</td></tr>
    <tr><td>5</td><td>Wang et al.</td><td>13.52</td><td>0.49</td></tr>
    <tr><td>6</td><td>EnlightenGAN</td><td>16.21</td><td>0.59</td></tr>
    <tr><td>7</td><td>Zero-DCE</td><td>16.57</td><td>0.59</td></tr>
    <tr>
      <td>8</td>
      <td><b>SubterraVision</b></td>
      <td><b>17.897</b></td>
      <td><b>0.57</b></td>
    </tr>
  </tbody>
</table>

<p align="center">
  <b>Table 2.</b>
  <em>Ablation study with training on SICE and validation on the ExDark dataset.</em>
</p>
<table align="center">
  <thead>
    <tr>
      <th>Information Flow</th>
      <th>Skip Connection</th>
      <th>Channel Attention</th>
      <th>PSNR</th>
      <th>SSIM</th>
      <th>LPIPS</th>
      <th>MPS</th>
      <th>NIQE</th>
      <th>BRISQUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Multi-path, uniform channel weights</td>
      <td>Yes</td>
      <td>No</td>
      <td>18.31</td>
      <td>0.6826</td>
      <td>0.1779</td>
      <td>0.7523</td>
      <td>4.4149</td>
      <td>19.65</td>
    </tr>
    <tr>
      <td>Multi-path + adaptive weighting</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>19.57</td>
      <td>0.7407</td>
      <td>0.1435</td>
      <td>0.7986</td>
      <td>4.4280</td>
      <td>18.48</td>
    </tr>
    <tr>
      <td>Curve Iteration = 4</td>
      <td>Yes</td>
      <td>Yes</td>
      <td><b>22.39</b></td>
      <td><b>0.8489</b></td>
      <td><b>0.0800</b></td>
      <td><b>0.8844</b></td>
      <td>4.5183</td>
      <td><b>18.09</b></td>
    </tr>
    <tr>
      <td>Curve Iteration = 8</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>19.28</td>
      <td>0.7316</td>
      <td>0.1487</td>
      <td>0.7914</td>
      <td>4.4171</td>
      <td>18.57</td>
    </tr>
    <tr>
      <td>Curve Iteration = 12</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>15.59</td>
      <td>0.5774</td>
      <td>0.2530</td>
      <td>0.6622</td>
      <td><b>4.3449</b></td>
      <td>22.01</td>
    </tr>
  </tbody>
</table>


### Visual Results
<p align="center">
<img width="1017" height="504" alt="image" src="https://github.com/user-attachments/assets/41ac054e-b306-4e73-9f48-f78d5201ee9d" />
<br>
<b>Figure 3.</b>
<em>
Visualization of SubterraVision with RGB channels.



## If you like this work, then consider citing

```
@article{tiwari2026subterravision,
  title={SubterraVision: A Computational Deep Learning Framework for Low-Light Image Enhancement in Underground Mining},
  author={Tiwari, Naveen Kumar and Bajpai, Abhishek and Singh, Nivedita},
  journal={Engineering Research Express},
  year={2026}
}
```


