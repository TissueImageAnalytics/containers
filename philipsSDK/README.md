# Philips SDK 2.0 Docker Container
Docker Image of the Philips SDK 2.0-L1 created for TIA Centre.

### Image Contents
Operating System: Ubuntu 20.04

Python Version: 3.8.10

Pip Version: 22.1.2

Linux Packages
1. libtiff5-dev

Extras  
Philips PathologySDK 2.0-L1 Research

### Pull the image from the Github Container Registry:
```bash
docker pull ghcr.io/tissueimageanalytics/philips-sdk:2.0l1
```
### Use the image as a base image in a Dockerfile:
```bash
FROM ghcr.io/tissueimageanalytics/philips-sdk:2.0l1
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
