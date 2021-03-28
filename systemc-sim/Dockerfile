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
RUN apt-get -y install libjpeg-dev 
RUN apt-get -y install libtiff-dev 
RUN apt-get -y install libtool 
RUN apt-get -y install m4 
RUN mkdir home/code 
ADD /test.cpp home/code 
RUN pip3 install simpy 
RUN pip3 install rpyc 
RUN pip3 install myhdl 
RUN pip3 install keras 
RUN pip3 install --upgrade tensorflow 
RUN pip3 install torch 
RUN echo "alias python='python3.8'" >> ~/.bashrc 
RUN . ~/.bashrc 
RUN git clone https://github.com/accellera-official/systemc.git home/systemc 
RUN mkdir home/systemc/objdir 
RUN mkdir /usr/local/systemc-2.3 
WORKDIR "/home/systemc" 
RUN libtoolize --force 
RUN aclocal 
RUN autoheader || true 
RUN automake --force-missing --add-missing 
RUN autoconf 
WORKDIR "/home/systemc/objdir" 
RUN ../configure --prefix=/usr/local/systemc-2.3 CXXFLAGS="-DSC_CPLUSPLUS=201402L" 
RUN make 
RUN make check 
RUN make install 
RUN export LD_LIBRARY_PATH=/usr/local/systemc-2.3/lib-linux64:$LD_LIBRARY_PATH 
RUN echo "export LD_LIBRARY_PATH=/usr/local/systemc-2.3/lib-linux64:\$LD_LIBRARY_PATH" >> ~/.bashrc 
RUN export SYSTEMC_HOME=/usr/local/systemc-2.3/ 
RUN echo "export SYSTEMC_HOME=/usr/local/systemc-2.3/" >> ~/.bashrc 
RUN . ~/.bashrc 
WORKDIR "/home/code" 
#RUN g++ -I. -I$SYSTEMC_HOME/include -L. -L$SYSTEMC_HOME/lib-linux64 -o out test.cpp -lsystemc -lm -std=c++14 
#RUN ./out
 
