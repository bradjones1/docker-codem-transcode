#codem transcode image
based on [dorftv/ffmpeg-core](https://registry.hub.docker.com/u/dorftv/ffmpeg-core/)

The image is built on the [automated docker hub](https://registry.hub.docker.com/u/dorftv/codem-transcode/). You can simple run it with

be sure to mount your file directory with the filedirectory in the container. if you want to override config.json use the -v option.

``` 
docker create --name codem  -it -p 8080:8080 --net host -v /srv/videos:/srv/videos  dorftv/codem-transcode
docker start codem
``` 

you can test the transcoder by rendering a Video
``` 
 curl -d '{"source_file": "/srv/videos/noise.mp4","destination_file":"/srv/videos/converted.mp4","encoder_options": "-vcodec libx264 -vb 416k -s 320x180 -y -threads 0"}' http://localhost:8080/jobs
```
