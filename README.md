# synodocker
docker-compose files for Synology
Docker Services for farmerbean.dev

From /volume2/docker/


sudo docker-compose up -d <service>

.env file for service environment variables

List of services 

pihole
lazydocker


Updating:

$sudo docker-compose pull
$sudo docker-compose up -d

Stopping:
$sudo docker-compose down


Networking


ip link add macvlan0 link eth0 type macvlan mode bridge # or ovs_eth0 if VMM is installed
ip addr add 192.168.1.192/27 dev macvlan0 # 192.168.1.192 - 192.168.1.223 255.255.255.224


sudo docker network create --driver=macvlan --gateway=192.168.1.1 --subnet=192.168.1.0/24  —-ip-range=192.168.1.192/28 --o parent=eth0 synoservices

