## Set up Detectron2 for GPU environment

1. Conda Environment
   ```
   conda create -n detectron2 python=3.6
   ```

1. Activate Anaconda environment
   ```
   conda activate detectron2
   ```

1. Install libraries with GPU dependencies
   ```
   conda install pytorch=1.3 torchvision cudatoolkit=10.0 -c pytorch
   ```

1. Install OpenCV
   ```
   conda install -c conda-forge opencv=4.1.0
   ```

1. Build Detectron2 and install it to your python environment
   ```
   python setup.py build develop
   ```

1. Download a video from Youtube
   ```
   pip install youtube-dl
   youtube-dl https://www.youtube.com/watch?v=rIh1iNxVGIc
   ```

1. Detectron2 Test
   
   Find config file in the [configs](./configs/) directory.
   
   Find weight path in the [model_zoo.py](./detectron2/model_zoo/model_zoo.py) file.

   mask example
   ```
   python demo/demo.py --config-file configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml \
   --video-input koi01.mkv \
   --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
   ```

   keypoint detection example
   ```
   python demo/demo.py --config-file configs/COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x.yaml \
   --video-input koi01.mkv \
   --opts MODEL.WEIGHTS detectron2://COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x/138363331/model_final_997cc7.pkl
   ```


## DensePose

1. Move to DensePose folder
   ```
   cd projects/DensePose
   ```

1. Download pre-trained model
   ```
   wget https://dl.fbaipublicfiles.com/densepose/densepose_rcnn_R_50_FPN_s1x/143908701/model_final_dd99d2.pkl
   ```

1. Run ApplyNet to visualize DensePose result
   ```
   python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_dd99d2.pkl image.jpg dp_contour,bbox --output image_densepose_contour.png

   python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_dd99d2.pkl image.jpg dp_contour,dp_segm --output image_densepose_contour.png
   ```

1. Run ApplyNet to visualize DensePose result on multiple images
   ```
   python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_dd99d2.pkl kill03c dp_contour,bbox --output kill03c_result/kill03c.png
   ```

1. Dump images in "images" folder into a pickle file
   ```
   python apply_net.py dump configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_dd99d2.pkl images --output dump.pkl -v
   ```


## Video File Management

1. Splitting a video file into jpg images
   ```
   ffmpeg -i input.mp4 images/%04d.jpg -hide_banner
   ```

1. Creating a video file
   ```
   ffmpeg -framerate 30 -i result_images/output.%4d.png -y output.mp4
   ```
