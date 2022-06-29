# Philips SDK 2.0 Docker Container
Docker Image of the PhilipsSDK2.0 created for the requirements of the [TIAToolbox](https://github.com/TissueImageAnalytics/tiatoolbox).

### Image Contents
Operating System: Ubuntu 18.04

Python Version: 3.6.9

Pip Version: 21.3.1

Linux Packages
1. libopenjp2-7-dev libopenjp2-tools
2. libtiff5-dev
3. openslide-tools
4. libgl1

Extras  
Philips PathologySDK 2.0 Research

### Pull the image from the Github Container Registry:
```bash
docker pull ghcr.io/tissueimageanalytics/philips-sdk:2.0
```
### Use the image as a base image in a Dockerfile:
```bash
FROM ghcr.io/tissueimageanalytics/philips-sdk:2.0
```
### Build the image locally:
1. Navigate to the Dockerfile that you want to use, based on the Python version and Operating System that you prefer

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
