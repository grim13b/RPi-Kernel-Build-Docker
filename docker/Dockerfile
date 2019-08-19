FROM ubuntu:18.04

RUN apt-get update && apt-get upgrade -y && apt-get install -y git bison flex libssl-dev build-essential bc gcc-aarch64-linux-gnu && rm -rf /var/lib/apt/lists/* 

RUN git clone --progress --verbose https://github.com/raspberrypi/tools.git --depth=1 ~/tools
ENV PATH $PATH:/root/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin

ENV BUILD_FOLDER /build
WORKDIR ${BUILD_FOLDER}
