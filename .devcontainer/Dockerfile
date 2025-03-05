# Use a stable Ubuntu LTS base image
FROM ubuntu:22.04

# Set noninteractive mode for APT
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install packages
RUN apt-get update && apt-get install -y \
    xfce4 xfce4-goodies xorg \
    xrdp \
    curl gnupg apt-transport-https \
    sudo \
    && apt-get clean

# Install Tailscale (using official script)
RUN curl -fsSL https://tailscale.com/install.sh | sh

# Configure xrdp to use XFCE session by default
RUN echo "startxfce4" > /etc/skel/.xsession

# Expose the RDP port
EXPOSE 3389

# Start xrdp in the foreground (adjust as needed)
CMD ["/usr/sbin/xrdp", "-n"]
