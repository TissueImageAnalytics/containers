# iSyntax2tiff Docker Container
Docker Image for converting iSyntax images to tiff

### Image Contents
Operating System: Ubuntu 20.04

Python Version: 3.8.10

Pip Version: 22.1.2

Linux Packages
1. libtiff5-dev

Extras  
Philips PathologySDK 2.0-L1 Research

### Instructions
Command for regular tiff from level 0 with batch size of 50:
```bash
python3 /app/isyntax_to_tiff.py <Isyntax file path> 0 0 0 50
```
  
Command for big tiff from level 0 with batch size of 100:
```bash
python3 /app/isyntax_to_tiff.py <Isyntax file path> 1 0 0 100
```

Command for regular sparse tiff from level 0 with batch size of 150:
```bash
python3 /app/isyntax_to_tiff.py <Isyntax file path> 0 1 0 150
```
Command for big sparse tiff from level 0 of batch size 50:
```bash
python3 /app/isyntax_to_tiff.py <Isyntax file path> 1 1 0 50
```

note: The converted image will be stored in the working directory from which the script was executed

### Pull the image from the Github Container Registry:
```bash
docker pull ghcr.io/tissueimageanalytics/isyntax2tiff:latest
```
### Use the image as a base image in a Dockerfile:
```bash
FROM ghcr.io/tissueimageanalytics/isyntax2tiff:latest
```
### Build the image locally:
1. Navigate to the Dockerfile

2. Build the Docker image
```bash
docker build -t <IMAGE_NAME> .       
```

3. Check that the image has been created
```bash
docker images 
```

4. Deploy the image as a Docker container
```bash
docker run -it --rm --name <CONTAINER_NAME> <IMAGE_NAME>     
```

5. Connect to the running container
```bash
docker exec -it <CONTAINER_NAME> bash
```

To add your own script and run it through the Docker container, first copy your script into the docker environment and then execute it.
```bash
COPY /path/to/<script>.py .
CMD ["python3", "<script>.py"]
```
