# VideoPose3D project with detectron2

This project is about estimating 3D human pose from customized 2D video, 
whose 2D keypoints are provided by detectron2 rather than detectron. 
This project is mainly about how to implement video-pose-3D project of facebook research 
for inference in the wild in your own computer. 
Instead of detectron, we use detectron2 here.

![Alt Text](https://github.com/DarrenJiang13/VideoPose3DwithDetectron2/blob/master/images/example.gif)

Reference: 
- [VideoPose3D Project](https://github.com/facebookresearch/VideoPose3D)
- [VideoPose3D_with_Detectron2](https://github.com/darkAlert/VideoPose3d_with_Detectron2)

## Configure your computer
0. Install ffmpeg imgMagick, see [this](https://github.com/DarrenJiang13/VideoPose3DwithDetectron2/blob/master/documents/VideoProcessConfiguration.md)
1. Install Nvidia Driver,CUDA10.1,cuDNN 7.6.5,pytorch, see [this](https://github.com/DarrenJiang13/VideoPose3DwithDetectron2/blob/master/documents/GPUConfiguration.md)
2. Install detectron2, see [this](https://github.com/DarrenJiang13/VideoPose3DwithDetectron2/blob/master/documents/Detectron2Installation.md)

## Dataset setup
1. download checkpoints
        
        # in the root directory, make a folder called checkpoint 
        mkdir checkpoint
        cd checkpoint
        wget https://dl.fbaipublicfiles.com/video-pose-3d/pretrained_h36m_detectron_coco.bin

2. download model for detectron2

        cd detectron2/detectron2-infer
        wget https://dl.fbaipublicfiles.com/detectron2/COCO-Keypoints/keypoint_rcnn_X_101_32x8d_FPN_3x/139686956/model_final_5ad38f.pkl

## Estimate your customized video
- Firstly, you should put the video you want into the `detectron2/detectron2-infer/videos` folder;
- Then:

        cd detectron2/detectron2-infer
- Run the `.sh` file:
        
        sh infer.sh videos/[your-video-name] [output-video-name-you-want]
- You shall see the output video in the `output` folder of the root directory.