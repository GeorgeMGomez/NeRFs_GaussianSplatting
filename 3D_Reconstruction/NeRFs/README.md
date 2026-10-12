# Reconstructing 3D Models with NeRFs by using Cloud services
All commands should be run in the cloud's code cell

## 1. Kaggle
Click the link to start using the cloud service Kaggle: https://www.kaggle.com/

## 2. Install COLMAP on Kaggle
Run the following command in the kaggle to install the Structure-from-Motion app 

```
!sudo apt-get update
!sudo apt-get install colmap
```

## 3. Install Nerfstudio
Installs Nerfstudio
```
!pip install nerfstudio 
```

## 4. Preparing folder structure
```
%cd /kaggle/working
!mkdir -p nerfstudio/custom_data/raw_images
```

## 5. Copying images to the raw_images folder
Click copy path on the folder(In input -> Datasets) containing the images and paste it in the "file path" section below
```
%cd /kaggle/working
!cp -r "file path"/*.jpg /kaggle/working/nerfstudio/custom_data/raw_images
```

## 6. Beginning Structure from Motion (SfM) process using COLMAP
```
!ns-process-data images --data /kaggle/working/nerfstudio/custom_data/raw_images --output-dir /kaggle/working/nerfstudio/custom_data --colmap-cmd colmap --no-gpu 
```

## 7. Training
Using 2 GPUs of Kaggle to train the NeRF model using nerfacto pipeline with 4096 rays per batch
```
!export CUDA_VISIBLE_DEVICES=0,1
!ns-train nerfacto --vis viewer --machine.num-devices 2 --pipeline.datamanager.train-num-rays-per-batch 4096  --data /kaggle/working/nerfstudio/custom_data
```

## 8. Zipping the output folder
Exporting the nerfstudio folder and outputs folder to a zip file for download
```
!zip -r /kaggle/working/nerfstudio_and_outputs.zip nerfstudio outputs
```

## 9. Pyngrok
Installing pyngrok to create a public URL for the viewer
```
!pip install pyngrok
```

## 10. Get Token
Create an account or sign in and copy the given token: https://ngrok.com/

## 11. View Result
Here we create the "network tunnel" which will allow the user to see the results from a cloud server.

```
#Importing the required libraries
import os
from pyngrok import ngrok

#Set your ngrok authtoken
ngrok.set_auth_token("Copy paste Token here")

#Open a tunnel to port 7007
public_url = ngrok.connect(7007)
print("Url to open the viewer:", public_url)

#Launch the viewer with the PyTorch 2.6 security override flag
os.system("TORCH_FORCE_NO_WEIGHTS_ONLY_LOAD=1 ns-viewer --load-config /kaggle/working/outputs/custom_data/nerfacto/2026-07-28_135747/config.yml")
```