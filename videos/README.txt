Add this folder structure -> objectName[folder] -> video of the object
To cut a video to pictures run this command: ffmpeg -i your_video.mp4 -vf "fps=2" ../Implementation/Gaussian_Split/folderName/images/frame_%04d.jpg
