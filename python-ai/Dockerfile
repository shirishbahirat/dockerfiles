FROM ubuntu:latest 
RUN apt-get update -y 
RUN apt-get install -y tzdata 
ENV TZ America/Denver 
RUN apt-get -y update 
RUN apt-get -y install software-properties-common 
RUN apt-get -y install build-essential 
RUN apt-get -y install git 
RUN apt-get -y install vim 
RUN apt-get -y install cmake 
RUN apt-get -y install python3.8 
RUN apt-get -y install python3-pip 
RUN apt-get -y install automake 
RUN apt-get -y install m4 
RUN mkdir home/code 
RUN pip3 install simpy 
RUN pip3 install rpyc 
RUN pip3 install myhdl 
RUN pip3 install keras 
RUN pip3 install --upgrade tensorflow 
RUN pip3 install torch torchvision
RUN echo "alias python='python3.8'" >> ~/.bashrc 
RUN . ~/.bashrc 
WORKDIR "/home/code" 
RUN apt-get install -y python3-opencv
RUN pip3 install opencv-contrib-python 
