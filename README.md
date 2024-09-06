# Training-free Online 3D Test-Time Adaptation via Denoising Diffusion Process

**Test-time adaptation (TTA)** of 3D point clouds is essential for addressing discrepancies between training and testing samples, particularly in corrupted point clouds like those from LiDAR data. Adapting models online to distribution shifts is crucial, as training for every variation is impractical. Existing methods often fine-tune models using self-supervised learning or pseudo-labeling, which can result in forgetting source domain knowledge.

We propose a training-free, online 3D TTA method called **3DD-TTA** (3D Denoising Diffusion Test-Time Adaptation), which adapts input point clouds using a diffusion strategy while keeping the source model unchanged. A Variational Autoencoder (VAE) encodes corrupted point clouds into latent spaces, followed by a denoising diffusion process. 

<p align="center">
  <img src="images/before-after.gif" alt="TTA of Pointcloud perturbed by Impulse Noise using 3DD-TTA">
</p>

![3DD-TTA Process](images/blockdiagram-v12-1.jpg)




## Key Features:
- **No fine-tuning required**: Keeps the source model intact.
- **Diffusion strategy**: Updates the corrupted latent points for alignment with the source domain.
- **Strong performance**: Achieves state-of-the-art results on ShapeNet, ModelNet40, and ScanObjectNN.

## Results:
Our method demonstrates superior generalization across multiple datasets, including ShapeNet, ModelNet40 and ScanObjectNN.

## Classification accuracies on ShapeNet-c


| Methods                  | uni  | gauss | back  | impu  | ups   | rbf   | rbf-i | den-d | den-i | shear | rot   | cut   | dist  | occ   | lidar | Mean  |
|--------------------------|------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| Point-MAE (src) [@point-mae] | 72.5 | 66.4  | 15.0  | 60.6  | 72.8  | 72.6  | 73.4  | 85.2  | 85.8  | 74.1  | 42.8  | _84.3_ | 71.7  | 8.4   | 4.3   | 59.3  |
| DUA [@dua]               | 76.1 | 70.1  | 14.3  | 60.9  | 76.2  | 71.6  | 72.9  | 80.0  | 83.8  | _77.1_ | **57.5** | 75.0  | 72.1  | 11.9  | 12.1  | 60.8  |
| TTT-Rot [@ttt-rot]       | 74.6 | 72.4  | _23.1_ | 59.9  | 74.9  | 73.8  | _75.0_ | 81.4  | 82.0  | 69.2  | 49.1  | 79.9  | 72.7  | _14.0_ | 12.0  | 60.9  |
| SHOT [@shot]             | 44.8 | 42.5  | 12.1  | 37.6  | 45.0  | 43.7  | 44.2  | 48.4  | 49.4  | 45.0  | 32.6  | 46.3  | 39.1  | 6.2   | 5.9   | 36.2  |
| T3A [@t3a]               | 70.0 | 60.5  | 6.5   | 40.7  | 67.8  | 67.2  | 68.5  | 79.5  | 79.9  | 72.7  | 42.9  | 79.1  | 66.8  | 7.7   | 5.6   | 54.4  |
| TENT [@tent]             | 44.5 | 42.9  | 12.4  | 38.0  | 44.6  | 43.3  | 44.3  | 48.7  | 49.4  | 45.7  | 34.8  | 48.6  | 43.0  | 10.0  | 10.9  | 37.4  |
| MATE-S [@mirza2023mate]  | _77.8_ | _74.7_ | 4.3   | _66.2_ | _78.6_ | _76.3_ | **75.3** | _86.1_ | _86.6_ | **79.2** | _56.1_ | _84.1_ | _76.1_ | 12.3  | _13.1_ | _63.1_ |
| 3DD-TTA (ours)           | **81.6** | **80.7** | **77.6** | **77.2** | **85.4** | **76.5** | **75.3** | **86.5** | **88.2** | 76.3  | 50.4  | **85.4** | **76.5** | **14.9** | **14.2** | **69.8** |


