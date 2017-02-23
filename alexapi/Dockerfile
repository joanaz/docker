FROM resin/rpi-raspbian:jessie-20160831  

RUN apt-get update && \  
    apt-get install git

WORKDIR /opt/ 

RUN git clone https://github.com/alexa-pi/AlexaPi.git

RUN ./AlexaPi/src/scripts/setup.sh
