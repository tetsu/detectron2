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

1. Download a video from Youtube
   ```
   pip install youtube-dl
   youtube-dl https://www.youtube.com/watch?v=rIh1iNxVGIc
   ```

1. Test demo
   ```
   python demo/demo.py --config-file configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml \
     --video-input {downloaded video file name} \
     --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
   ```