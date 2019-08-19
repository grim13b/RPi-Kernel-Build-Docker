# RaspberryPi KernelBuild用 Docker Container

## これは何

RPi KernelをCrossCompileするためのDockerContainerです。  

## 使い方

基本的には公式のビルド手順に準拠します。  
[Kernel building](https://www.raspberrypi.org/documentation/linux/kernel/building.md)

### Dockerfileを持ってくる

copy and pastでもいいですし、このrepoをcloneしてもいいです。  

### ContainerImageをbuildする

```
$ docker build --tag [containername]:[revision] .
```

containernameとrevisionは適宜決めてください。  
最後の.はtypoじゃないので注意してください。  
詳細はdocker --helpを参照してください。

### Kernelのソースコードを持ってくる

公式の Get sources を参照してください。

### Containerをrunする

-v で先に持ってきたkernelのSourceCodeをContainerにAttachします。  

```
$ docker run -it --rm -v [Localに持ってきたKernelSourceCodeのPath]:/build [containername:revision] /bin/bash
```

### Container内でmakeする

公式の Build sources を参照してください。  
必要なLibやDependsはInstall済みなので省略して問題ありません。  

RPi3Bの場合は以下のような感じです。  

```
$ KERNEL=kernel7
$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig
$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
```

