FROM python:3.7-slim

RUN apt-get update
RUN apt-get install -y cmake git libgtk2.0-dev pkg-config libavcodec-dev \
libavformat-dev libswscale-dev python-dev python-numpy libtbb2 libtbb-dev \
libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev unzip

RUN apt-get install -y wget

RUN cd \
    && wget https://github.com/opencv/opencv/archive/3.2.0.zip \
    && unzip 3.2.0.zip \
    && cd opencv-3.2.0 \
    && mkdir build \
    && cd build \
    && cmake .. \
    && make -j8 \
    && make install \
    && cd \
    && rm 3.2.0.zip \
    && rm -rf opencv-3.2.0


RUN pip3 install keras tensorflow numpy scipy pillow matplotlib h5py
RUN pip3 install opencv-python
RUN pip3 install https://github.com/OlafenwaMoses/ImageAI/releases/download/2.0.2/imageai-2.0.2-py3-none-any.whl 

RUN mkdir /app
ADD webcam.py /app/
ADD yolo.h5 /app/
WORKDIR /app

ENTRYPOINT /usr/local/bin/python3 webcam.py
