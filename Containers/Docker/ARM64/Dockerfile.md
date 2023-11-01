# Dockerfile
* * *

## Unbuntu base image for ARM64
To perform fuzzing on binaries compiled for the ARM 64 architecture, it's necessary to configure our environment to be compatible with ARM. We will accomplish this by using the "arm64v8/ubuntu" base image. However, there's a challenge here – the host architecture is x86_64, and we aim to create a container for ARM64. To address this disparity, we must employ an emulation method, such as QEMU, to simulate ARM64 within the container. 

- qemu-user-static provides the actual binary emulation capabilities for running binaries compiled for different CPU architectures.
- binfmt-support helps to register handlers for various binary formats so that the Linux kernel can correctly identify the format and invoke the appropriate interpreter or emulator (like QEMU) when executing a binary of an unknown or foreign architecture.

### On Host
```
# Update & install required packages
sudo apt-get update && sudo apt-get install -y \
	qemu-user-static \
	binfmt-support
	
# Set up QEMU within a Docker container
docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
```

### Dockerfile
```
# Specify a base image (Ubuntu 20.04 LTS image optimized for ARM 64-bit)
FROM arm64v8/ubuntu:20.04

# Install dependencies
RUN apt-get update
RUN apt-get install -y \
	wget \
	git \
	make \
	build-essential \
	clang \
	llvm \
	nano \
	python3-dev\
	ninja-build \
	libglib2.0-dev \
	pkg-config

# Install GCC headers
RUN apt install -y gcc-$(gcc --version|head -n1|sed 's/\..*//'|sed 's/.* //')-plugin-dev libstdc++-$(gcc --version|head -n1|sed 's/\..*//'|sed 's/.* //')-dev

# Create a directory to store your fuzzing work.
WORKDIR /work

# Start a shell for interactive use.
CMD ["/bin/bash"]
```
