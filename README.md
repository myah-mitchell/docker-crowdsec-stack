# Docker Crowdsec Stack


## Create needed folders

```bash
mkdir -p /opt/docker/volumes/crowdsec/crowdsec-config
mkdir -p /opt/docker/volumes/crowdsec/crowdsec-data
chmod -R 770 /opt/docker/volumes/crowdsec/*
sudo chown -R $USER:101000 /opt/docker/volumes/crowdsec
sudo chown -R 101000:101000 /opt/docker/volumes/crowdsec/crowdsec*
```

The mounts to the files in ./crowdsec-config will have to be disabled prior to the first start of the stack. After that the mounts can be added back.