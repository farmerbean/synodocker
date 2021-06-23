# YouTubeDL-Material Service
Service environment variables are in ~/.env
 - IP address of service
 - Custom path for Video downloads (Docker running on small partition)
## Services:
 - YouTubeDL-Material
 - GitHub repo [github.com](https://github.com/Tzahi12345/YoutubeDL-Material)

## Configuration
This service was configured using the docker-compose file from YoutubeDL-Material v4.2 which is slightly different to the configuration on the main README (see tag:nightly and ports). Because I wanted to drop videos into Plex and use a different drive for data, there was some drama getting the right permissions on that folder. The /app/video permissions required me to exec into the container and set permissions on the host folder manually (please don't tell anyone) as follows:

 1. Create source folder outside Docker Working Directory
 2. Modify its permission to grant docker group full permissions
 3. Exec into container as root
 4. Chmod /app/video permission 755
 5. Chown /app/video to user youtube
 6. Chgrp /app/video to user youtube
 
Forgive me, lord.
