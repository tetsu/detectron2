## DensePose Samples

densepose_rcnn_R_50_FPN_s1x
```
python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml densepose_rcnn_R_50_FPN_s1x.pkl image.jpg dp_contour,bbox --output densepose_rcnn_R_50_FPN_s1x.png
```

densepose_rcnn_R_101_FPN_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_s1x.yaml densepose_rcnn_R_101_FPN_s1x.pkl image.jpg dp_contour,bbox --output densepose_rcnn_R_101_FPN_s1x.png
```

densepose_rcnn_R_101_FPN_DL_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_s1x.yaml densepose_rcnn_R_101_FPN_DL_s1x.pkl image.jpg dp_contour,bbox --output densepose_rcnn_R_101_FPN_DL_s1x.png
```

densepose_rcnn_R_101_FPN_DL_WC1_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_WC1_s1x.yaml densepose_rcnn_R_101_FPN_DL_WC1_s1x.pkl image.jpg dp_contour,bbox --output densepose_rcnn_R_101_FPN_DL_WC1_s1x.png

```

densepose_rcnn_R_101_FPN_DL_WC2_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_WC2_s1x.yaml densepose_rcnn_R_101_FPN_DL_WC2_s1x.pkl image.jpg dp_contour,bbox --output densepose_rcnn_R_101_FPN_DL_WC2_s1x.png
```

## Split video file with ffmpeg
```
ffmpeg -i GESREC_Youtube.mp4 -vcodec png split_images/GESREC_Youtube/GESREC_%05d.png

ffmpeg -i kprgM0bvHNo.mp4 -vcodec png split_images/kprgM0bvHNo/kprgM0bvHNo_%05d.png

kprgM0bvHNo
```

## Infer multiple images with densepose_rcnn_R_101_FPN_DL_WC2_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_WC2_s1x.yaml densepose_rcnn_R_101_FPN_DL_WC2_s1x.pkl split_images/GESREC_Youtube dp_contour,bbox --output inferred_images/GESREC_Youtube/image.png
```

Combine images files to a video file with ffmpeg (24fps, mp4)
```
ffmpeg -r 24 -i inferred_images/GESREC_Youtube/image.%04d.png -vcodec libx264 -pix_fmt yuv420p -r 24 inferred_videos/GESREC_Youtube_inferred.mp4
```

## Infer multiple images with densepose_rcnn_R_101_FPN_s1x
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_s1x.yaml densepose_rcnn_R_101_FPN_s1x.pkl split_images/GESREC_Youtube dp_contour,bbox --output inferred_images/R_101_FPN/image.png
```

Combine images files to a video file with ffmpeg (24fps, mp4)
```
ffmpeg -r 24 -i inferred_images/R_101_FPN/image.%04d.png -vcodec libx264 -pix_fmt yuv420p -r 24 inferred_videos/GESREC_Youtube_R_101_FPN.mp4
```


## other
```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_s1x.yaml densepose_rcnn_R_101_FPN_s1x.pkl split_images/GESREC_Youtube/GESREC_00385.png dp_contour,bbox --output inferred_images/image.png
```

```
python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_WC2_s1x.yaml densepose_rcnn_R_101_FPN_DL_WC2_s1x.pkl split_images/GESREC_Youtube dp_contour,bbox --output inferred_images/GESREC_YoutubeR_101_FPN_DL_WC2_s1x/image.png
```

Combine images files to a video file with ffmpeg (24fps, mp4)
```
ffmpeg -r 24 -i inferred_images/GESREC_YoutubeR_101_FPN_DL_WC2_s1x/image.%04d.png -vcodec libx264 -pix_fmt yuv420p -r 24 inferred_videos/GESREC_Youtube_R_101_FPN_DL_WC2_s1x.mp4

ffmpeg -r 60 -i inferred_images/kprgM0bvHNo/image.%04d.png -vcodec libx264 -pix_fmt yuv420p -r 60 inferred_videos/kprgM0bvHNo.mp4
```


python apply_net.py show configs/densepose_rcnn_R_101_FPN_DL_WC2_s1x.yaml densepose_rcnn_R_101_FPN_DL_WC2_s1x.pkl split_images/kprgM0bvHNo dp_contour,bbox --output inferred_images/kprgM0bvHNo/image.png