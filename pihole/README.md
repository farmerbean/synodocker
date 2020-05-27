# Pi-hole Service for farmerbean.dev
Service environment  variables are in ~/.env
## Services:
 - pi-hole

## Create TLS Certs for Web Interface

    $ sudo cat /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.key \
    /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.cer | \
    sudo tee /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.combined.pem
