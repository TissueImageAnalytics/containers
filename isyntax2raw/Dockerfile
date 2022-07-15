# Start from PhilipsSDK image from TIALAB
FROM ghcr.io/tissueimageanalytics/philips-sdk:2.0l1

COPY ./isyntax2raw-0.4.0.post21.dev173556795-py3-none-any.whl .

RUN pip3 install --no-cache-dir numpy isyntax2raw-0.4.0.post21.dev173556795-py3-none-any.whl zarr_jpeg2k

ENTRYPOINT [ "sh", "-c" ]
