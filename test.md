
R-CNN MASK to save as images
```
python demo/demo.py --config-file configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml \
  --video-input cant_feel_my_face.webm \
  --output ./output \
  --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl


python demo/demo.py --config-file configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml \
  --video-input iOS.MP4 \
  --output ./output/iOS-03.mkv \
  --confidence-threshold 0.9 \
  --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```

Combine images files to a video file with ffmpeg (24fps, mp4)
```
ffmpeg -r 29.97 -i ./output/output_%04d.png -vcodec libx264 -pix_fmt yuv420p -r 29.97 cant.mp4
```

python process_video.py -i cant_feel_my_face.webm -p -d -ov cant.avi