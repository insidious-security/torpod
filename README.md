<p align="center">
  <img src="https://img.shields.io/github/last-commit/insidious-security/torpod.svg?style=for-the-badge">
  <img src="https://img.shields.io/github/license/insidious-security/easyssh?style=for-the-badge">
</p>

# Torpod
This Dockerfile sets up a secure docker container, creates a single username and is anonymously accessible from the tor network.
To use this container you'll need to have [Docker](https://www.docker.com/) installed on your system. The connecting client needs to have the following packages:
- tor
- torify
- torsocks

Install the required packages:
```bash
# Debian based systems:
$ sudo apt install tor torify --yes

# Arch based systems:
$ sudo pacman -S tor torify --noconfirm

# Redhad
$ dnf install tor torify
```

## Usage:
```bash
# Clone this repository:
$ git clone https://github.com/insidious-security/torpod.git

# Change to torpod directory:
$ cd torpod/

# Change the username and password in the Dockerfile.
line 8: RUN echo "username:changeme" | chpasswd

# Build and run the container:
$ docker build -t torpod:latest .
$ docker run --name torpod -dit torpod:latest

# Check the container status:
$ docker ps -a

# Get the onion hostname:
$ docker exec torpod cat /var/lib/tor/onion-ssh/hostname

# Connecting:    
# Make sure tor.service is running on your connecting client..    
$ torify ssh sidious@owhfjwncoiwncoewncowencojwncoic.this.is.an.example.address.onion
```
