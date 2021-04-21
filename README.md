# synodocker

This is my docker-compose repo for spinning up Docker services on Synology NAS (DS1515+ with DSM6.x). There are three accompanying medium.com stories that relate to this repo that cover:

 1. Configuring DDNS with Cloudflare and generating a TLS certificate
 2. Configuring macvlan networking on Synology for Docker containers
 3. Configuring pi-hole - [medium.com](https://medium.com/@corcoran/installing-pihole-with-docker-on-synology-nas-dsm6-e77f4f0dcb58)

## Docker Services for farmerbean.dev
Service environment  variables are in ~/.env
### Services:
 - lazydocker
 - portainer
 - pi-hole
 - auto-YouTube-Downloader
 - phpipam
 - MySQL (for phpipam)
 
## Start/Stop Services
     $ sudo docker-compose up -d <service>
     $ sudo docker-compose down -d <service>

## Updating

    $ sudo docker-compose pull
    
    $ sudo docker-compose up -d  

## Networking  

Refer to [this story](https://medium.com/@corcoran/docker-with-macvlan-networking-on-synology-dsm6-741285a0297d?source=---------4------------------)

### Basic execution
I'm assuming your internal physical network is 192.168.1.x . Confine your internal DHCP scope if possible to avoid clashes when deploying your containers. The [ip] commands  deal with creating a virtual lan that bridges your physical network, the docker network commands deal with understanding what the host (physical) network looks like:

    $ ip link add macvlan0 link eth0 type macvlan mode bridge
    $ ip addr add 192.168.1.192/27 dev macvlan0 # 192.168.1.192 - 192.168.1.223 255.255.255.224

Then (synoservices is the name of the docker network here)

    $ sudo docker network create --driver=macvlan --gateway=192.168.1.1 --subnet=192.168.1.0/24 —-ip-range=192.168.1.192/27 --o parent=eth0 synoservices

You can remove this afterwards running:

    $ sudo docker network remove synoservices

> Written with [StackEdit](https://stackedit.io/).
