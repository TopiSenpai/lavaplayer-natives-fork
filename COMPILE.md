# Compile Lavaplayer native libraries

## Requirements

Install Docker: https://docs.docker.com/engine/install

Install QEMU, binfmt-support and qemu-user-static

```bash
$ sudo apt install qemu binfmt-support qemu-user-static 
```

### Linux (glibc)

#### x86

```bash
$ docker run --rm -it --platform linux/386 -v ./:/build i386/debian:10 bash
$ apt update && apt install -y openjdk-11-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

#### x86-64

```bash
$ docker run --rm -it --platform linux/amd64 -v ./:/build amd64/debian:10 bash
$ apt update && apt install -y openjdk-11-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

#### arm

```bash
$ docker run --rm -it --platform linux/arm/v7 -v ./:/build arm32v5/debian:10 bash
$ apt update && apt install -y openjdk-11-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

#### armhf

```bash
$ docker run --rm -it --platform linux/arm/v6 -v ./:/build arm32v6/debian:10 bash
$ apt update && apt install -y openjdk-8-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

#### aarch32

```bash
$ docker run --rm -it --platform linux/arm/v8 -v ./:/build arm32v7/debian:10 bash
$ apt update && apt install -y openjdk-8-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

#### aaarch64

```bash
$ docker run --rm -it --platform linux/arm64/v8 -v ./:/build arm64v8/debian:10 bash
$ apt update && apt install -y openjdk-8-jdk-headless
$ cd /build
$ ./gradlew compileNatives
```

### Linux (musl)

#### x86-64

```sh
# docker run --rm -it --platform linux/amd64 amd64/alpine sh

# apk update && apk upgrade
# apk add git cmake build-base autoconf openjdk8 wget

# wget https://mirror2.sandyriver.net/pub/software/gnu/automake/automake-1.15.1.tar.gz
# tar -zxvf automake-1.15.1.tar.gz
# cd automake-1.15.1
# ./configure
# make install

# cd ..
# git clone https://github.com/Walkyst/lavaplayer-natives-fork
# cd lavaplayer-natives-fork
# chmod +x ./gradlew
# ./gradlew load
# touch natives/opus/opus-1.3/aclocal.m4 configure
# ./gradlew compileNatives
```

#### aaarch64

```sh
# docker run --rm -it --platform linux/arm64/v8 arm64v8/alpine sh

# apk update && apk upgrade
# apk add git cmake build-base autoconf openjdk8 wget

# wget https://mirror2.sandyriver.net/pub/software/gnu/automake/automake-1.15.1.tar.gz
# tar -zxvf automake-1.15.1.tar.gz
# cd automake-1.15.1
# ./configure
# make install

# cd ..
# git clone https://github.com/Walkyst/lavaplayer-natives-fork
# cd lavaplayer-natives-fork
# chmod +x ./gradlew
# ./gradlew load
# touch natives/opus/opus-1.3/aclocal.m4 configure
# ./gradlew compileNatives
```

### Windows

```bash
$ gradlew.bat build
```

### Mac OS X

```bash
$ ./gradlew build
```