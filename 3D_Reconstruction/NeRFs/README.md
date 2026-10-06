# Reconstructing 3D Models with NeRFs

## 1. Kaggle
Click the link to start using the cloud service Kaggle: https://www.kaggle.com/

## 2. Install COLMAP on Kaggle
Run the following command in the kaggle to install the app that processes Structure-from-Motion

```
!sudo apt-get update
!sudo apt-get install colmap
```

## 3. Install Nerfstudio
```
!pip install nerfstudio 
```

## 4. Preparation of Folders
Creates a folder nerfstudio/custom_data/raw_images where your pictures from the Input Section of Kaggle are copied to the raw_images folder.

```
!mkdir -p nerfstudio/custom_data/raw_images 
!cp HerePutTheAddressToYourImagesInInputSection/*.jpg 
/kaggle/working/nerfstudio/custom_data/raw_images/
```

## 5. Initiating Structure from Motion from Colmap
```
!ns-process-data images --data /kaggle/working/nerfstudio/custom_data/raw_images --output-dir 
/kaggle/working/nerfstudio/custom_data --colmap-cmd colmap --no-gpu
```

## 6. Begin Training process
```
!ns-train nerfacto --vis viewer --machine.num-devices 2 --pipeline.datamanager.train-num-rays
per-batch 4096  --data /kaggle/working/nerfstudio/custom_data 
```



