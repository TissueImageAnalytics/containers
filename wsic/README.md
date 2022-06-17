# jp2tiff

Create the Docker container run 
```bash
docker build -t <image_name> .
```

Run the container with the pre-defined command
```bash
docker run -d \       
  -it \
  --name <container_name> \
  --mount type=bind,source=<path_to_file>,target=/workspace \                                                                                   
-e input=1.jp2 -e output=1.tiff <image_name>
```

Run the container by specifying the full command
```bash
docker run -d \       
  -it \
  --name <container_name> \
  --mount type=bind,source=<path_to_file>,target=/workspace \                                                                         
<image_name> "wsic convert -i 1.jp2 -o 1.tiff -rt 4096 4096 -w 4 --no-ome --overwrite -to 30"
```

Pull the container from my private docker hub registry
```bash
docker pull ghadjigeorgiou/wsic:latest
```
