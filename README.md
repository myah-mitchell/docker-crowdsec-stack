# Docker Crowdsec Stack


## Create needed folders

```bash
mkdir -p /opt/docker/volumes/crowdsec/crowdsec-config
chmod -R 770 /opt/docker/volumes/crowdsec/*
sudo chown -R $USER:101000 /opt/docker/volumes/crowdsec
sudo chown -R 101000:101000 /opt/docker/volumes/crowdsec/crowdsec*
```

Create a file at `/opt/docker/volumes/crowdsec/crowdsec-config/parsers/s02-enrich/custom-whitelist.yaml` and add the following content:

```
name: crowdsecurity/whitelists
description: "Whitelist events from my ip addresses"
whitelist:
  reason: "my ip ranges"
  ip:
    - "127.0.0.1" # Local Host
  cidr:
    - "192.168.0.0/16" # Local IPs
    - "10.0.0.0/8" # Local IPs
    - "172.16.0.0/12" # Local/Docker IPs
```

## To Enroll the Server
Run the following:

```
cscli console enroll <EnrollToken>
```

## Helpful Commands

To generate an API Key for a Traefik Bouncer run:

```
docker exec -t crowdsec cscli bouncers add traefik-bouncer-<hostname>
```

To generate a maching login for a Crowsec Satellite run:

```
cscli machines add <ContainerCrowdsec CUSTOM_HOSTNAME> --auto -f /tmp/crowdsec.yaml
cat /tmp/crowdsec.yaml
rm /tmp/crowdsec.yaml
```