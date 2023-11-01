# Dockerfile
* * *
## Standard Kali base image
```
# Use an official base image with Kali Linux.
FROM kalilinux/kali-rolling

# Update the package list
RUN apt update

# Install dependencies

# Create a directory to store your work.
WORKDIR /work

# Set the entry point to /bin/bash.
CMD ["/bin/bash"]
```
