# Reconstructing 3D Models with Gaussian Splatting on Local Pc

## 1. Install WSL
Follow the instructions to install WSL here: https://learn.microsoft.com/en-us/windows/wsl/install

## 2. Terminal
Open terminal and switch to Ubuntu

## 3. Installation Colmap
Inside the ubuntu terminal run these commands below
```
sudo apt update
sudo apt install -y colmap
```
After the installation finishes run
```
colmap gui
```
To open the app

## 4. Colmap App
Click Reconstruction -> Automatic reconstruction.
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush1.png?raw=true)
In the Workspace select the folder{Object_name} that contains the image folder
The structure should be like this
```
--Object_name
    --images
```
Inside the images folder should be the raw images of the object
Then  in the image select the images folder
Click run
Adjust the quality so it does not exceed your GPUs VRAM and crash
If the problem persists then resize your raw images to lower resolution
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush2.png?raw=true)

With the structure from motion complete a sparse folder is created automatically
in the workspace folder and a database.db
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush3.png?raw=true)

## 5. Install Brush App
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush4.png?raw=true)

If using windows select second option
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush5.png?raw=true)

Click brush_app.exe to open the app
![image_alt](https://github.com/GeorgeMGomez/NeRFs_GaussianSplatting/blob/main/3D_Reconstruction/GaussianSplatsLocal/imagesForREADME/brush6.png?raw=true)

## 6. Brush training
Click Directory or File and select your workspace folder which contains the sparse folder and click run to begin training. After it finishes you can save it as a ".ply" format and view it here: https://superspl.at/editor
