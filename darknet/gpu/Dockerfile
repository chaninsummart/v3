FROM nvidia/cuda:11.0-cudnn8-devel-ubuntu18.04-rc


MAINTAINER Chanin 

# working directory
WORKDIR /darknet

# install
RUN \
	apt-get update && apt-get install -y \
	autoconf \
        automake \
	libtool \
	build-essential \
	git

# addons
RUN \
	apt-get install -y \
	wget

# build repo
RUN \
	git clone https://github.com/pjreddie/darknet

WORKDIR D:\CAT\docker\darknet\gpu\Dockerfile
COPY ./Makefile ./
RUN \
	sed -i 's/GPU=.*/GPU=1/' Makefile && \
	make

# download weights full (accurate most) and tiny (faster , less accurate) models
# darknet rnns
RUN \ 
	wget http://pjreddie.com/media/files/yolo.weights >/dev/null 2>&1 && \
	wget http://pjreddie.com/media/files/yolo9000.weights >/dev/null 2>&1 && \
	wget http://pjreddie.com/media/files/tiny-yolo-voc.weights >/dev/null 2>&1
	
# darknet nightmare	
RUN \ 
	wget http://pjreddie.com/media/files/vgg-conv.weights >/dev/null 2>&1

# darknet rnns
RUN \
	wget http://pjreddie.com/media/files/shakespeare.weights >/dev/null 2>&1 && \
	wget http://pjreddie.com/media/files/grrm.weights >/dev/null 2>&1 && \
	wget http://pjreddie.com/media/files/tolstoy.weights >/dev/null 2>&1 && \
	wget http://pjreddie.com/media/files/kant.weights >/dev/null 2>&1

# darknet rnns train shakespeare
RUN \
	wget https://ocw.mit.edu/ans7870/6/6.006/s08/lecturenotes/files/t8.shakespeare.txt >/dev/null 2>&1

# darknet go
RUN \
	wget pjreddie.com/media/files/go.weights >/dev/null 2>&1

# test nvidia docker
#CMD nvidia-smi -q

# defaults command
CMD ["bash"]

