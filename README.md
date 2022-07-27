# Torpod
To use this container you'll need to have docker installed on your system. The connecting client needs to have the following packages:
- tor
- torify
- torsocks

## The repository:
This Dockerfile sets up a secure docker container, creates a single username and is anonymously accessible from the tor network.

## Usage:
```bash
# Clone this repository:
$ git clone https://github.com/insidious-security/torpod.git

# Change to torpod directory:
$ cd torpod/

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
