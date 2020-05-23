# Create TLS Certs for Web Interface
```

sudo cat /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.key \
           /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.cer | \
  sudo tee /usr/local/share/acme.sh/syno.farmerbean.dev/syno.farmerbean.dev.combined.pem

```

Sources:

https://discourse.pi-hole.net/t/setup-on-synology-docker/18067/33

https://gist.github.com/xirixiz/ecad37bac9a07c2a1204ab4f9a17db3c
