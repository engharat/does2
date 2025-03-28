# DC_DOES: Double Camera Orientation Estimation (of roll and pitch) at Sea
Code from the paper "DC-DOES: A Dual-Camera Deep Learning Approach for Robust Orientation Estimation in Maritime Environments". 

All the instructions to correctly run DOES can be found in the [instruction.md](./instruction.md) file.
If you wish to try DC-DOES on a custom dataset, keep in mind that probably a basic finetuning of the model weights will be necessary to obtain good results! For this reason, we suggest to make a first training on the DC-ROPIS datasets (also to further verify if it correctly runs) *having prior modified the script to save and load the weights*. At this point, you can proceed with the tuning.

If you liked our work and you wish to use it in your research, please cite us!

### Original Articles

> **Di Ciaccio, F., Troisi, S., & Russo, P. (2024). DC-DOES: A Dual-Camera Deep Learning Approach for Robust Orientation Estimation in Maritime Environments. IEEE Access.**

> @article{di2024dc,
  title={DC-DOES: A Dual-Camera Deep Learning Approach for Robust Orientation Estimation in Maritime Environments},
  author={Di Ciaccio, Fabiana and Troisi, Salvatore and Russo, Paolo},
  journal={IEEE Access},
  year={2024},
  publisher={IEEE}
}

> **Di Ciaccio, F., Russo, P., & Troisi, S. (2022). Does: A deep learning-based approach to estimate roll and pitch at sea. IEEE access, 10, 29307-29321.**

> @article{di2022does,
  title={Does: A deep learning-based approach to estimate roll and pitch at sea},
  author={Di Ciaccio, Fabiana and Russo, Paolo and Troisi, Salvatore},
  journal={IEEE access},
  volume={10},
  pages={29307--29321},
  year={2022},
  publisher={IEEE}
}

### Conference paper
> **Russo, P., & Di Ciaccio, F. (2022, October). Deep models optimization on embedded devices to improve the orientation estimation task at sea. In 2022 IEEE International Workshop on Metrology for the Sea; Learning to Measure Sea Health Parameters (MetroSea) (pp. 44-49). IEEE.**

> @inproceedings{russo2022deep,
  title={Deep models optimization on embedded devices to improve the orientation estimation task at sea},
  author={Russo, Paolo and Di Ciaccio, Fabiana},
  booktitle={2022 IEEE International Workshop on Metrology for the Sea; Learning to Measure Sea Health Parameters (MetroSea)},
  pages={44--49},
  year={2022},
  organization={IEEE}
}


# DC-DOES: Overview
DC-DOES is a Deep Learning model designed to enhance orientation estimation in maritime navigation. DC-DOES builds upon the previous model [1], improving performance by incorporating a dual-camera setup and a low-cost AHRS sensor integrated into a fully customizable embedded Linux-based device. Moreover, the novel dataset **Double Camera - ROll and PItch at Sea (DC-ROPIS)**, which contains paired images and corresponding orientation ground truth, was collected specifically for this purpose.
The approach aims to improve robustness in traditional methods under specific conditions, such as GNSS signal unavailability or long-lasting outages that cause significant drift in inertial sensors. It also addresses potential confusion with nearby robots equipped with SONAR or RADAR systems. However, DC-DOES is not intended to replace current systems but rather to complement them. 
Once deployed, DC-DOES relies entirely on visual features, making it immune to sensor drift over time. During deployment, the system architecture does not depend on AHRS, which is only used during the training phase.
<!--- ### DANAE Roll estimation - OXIO Dataset

![plot](./Results_Figure/oxford_LKF_phi.jpg)
![plot](./Results_Figure/oxford_danae1_phi.jpg)

### DANAE Pitch estimation - UCS Dataset
![plot](./Results_Figure/ucs_lkf_theta.jpg)
![plot](./Results_Figure/ucs_danae1_theta.jpg)

DANAE++ is the enhanced version of the first architecture: it is able to denoise IMU/AHRS data obtained through both the Linear (LKF) and Extended (EKF) Kalman filter-derived values. Better results are achieved by DANAE++ also when compared to common low-pass filters (in our study, the [Butter LP filter](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.butter.html
) and the [Uniform1d filter](https://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.uniform_filter.html) both provided by the Scipy library).

The following images shows the results obtained by DANAE++ w.r.t. the roll angle estimation provided by the EKF and the LP filters for the OXIO Dataset, together with DANAE++ performance on the pitch angle estimation for the UCS Dataset.

### DANAE++ Roll estimation - OXIO Dataset
![plot](./Results_Figure/oxford_EKF_phi.jpg)
![plot](./Results_Figure/oxford_danae++_phi.jpg)
![plot](./Results_Figure/comparative_filters_butter_phi.jpg)
![plot](./Results_Figure/comparative_filters_uniform_phi.jpg)

### DANAE++ Pitch estimation - UCS Dataset
![plot](./Results_Figure/ucs_ekf_theta.jpg)
![plot](./Results_Figure/ucs_danae++_theta.jpg) ... -->


# DC-ROPIS Dataset

The **DC-ROPIS dataset** can be downloaded from the following link:  
🔗 [Download DC-ROPIS Dataset](https://studentiuniparthenope-my.sharepoint.com/:u:/g/personal/fabiana_diciaccio_studenti_uniparthenope_it/EUL0gccLZ21Fhn0B83ixg5IBNHkFRINY7qP1v4ThdPpf2g?e=8Jt3lC)

## 📂 Dataset Structure

The dataset is organized into two main directories:

- **`train/`** – Contains training samples  
- **`test/`** – Contains test samples  

Each directory is further divided into subdirectories based on different acquisition settings.

### 📁 Contents of Each Subdirectory

Each subdirectory includes:

- 📷 **Image samples** – Captured under specific acquisition conditions  
- 📄 **`data.txt`** – A metadata file containing ground truth values:
  - **Roll**
  - **Pitch**
  - Additional parameters
