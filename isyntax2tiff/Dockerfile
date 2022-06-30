# Start from PhilipsSDK image from TIALAB
FROM ghcr.io/tissueimageanalytics/philips-sdk:2.0l1

# Copy scripts for converting isyntax to tiff
WORKDIR /app
COPY ./isyntax_to_tiff.py .
COPY ./libtiff_interface.py .

#Install numpy note: If more dependencies are required use a requirements.txt file
RUN pip3 install --no-cache-dir numpy

ENTRYPOINT [ "sh", "-c" ]
