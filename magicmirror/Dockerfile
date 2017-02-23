FROM resin/rpi-raspbian:jessie-20160831  

RUN apt-get update && \  
    apt-get -qy install curl

RUN curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
RUN apt-get install -y nodejs
RUN apt-get install -y build-essential

RUN apt-get install git

RUN apt-get upgrade

RUN apt-get install build-essential cmake pkg-config
RUN apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
RUN apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
RUN apt-get install libxvidcore-dev libx264-dev
RUN apt-get install libgtk2.0-dev
RUN apt-get install python2.7-dev python3-dev

RUN wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.1.0.zip
RUN unzip opencv.zip

RUN wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.1.0.zip
RUN unzip opencv_contrib.zip

RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py

RUN pip install numpy

WORKDIR /opencv-3.1.0/
RUN mkdir build
WORKDIR /build
RUN cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.1.0/modules \
    -D BUILD_EXAMPLES=ON ..

RUN make -j4

RUN make install
RUN ldconfig

RUN curl -sL https://raw.githubusercontent.com/MichMich/MagicMirror/master/installers/raspberry.sh | bash


