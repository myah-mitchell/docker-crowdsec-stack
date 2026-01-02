# Docker Crowdsec Stack

## First boot

1. Edit the compose file and comment out the volumes referencing files from crowdsec-config
2. Let the container fully start and create the initial config for the container.
3. Restore the compose file to the original state and start the container again.


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
cscli machines add <hostname> --auto -f /tmp/crowdsec.yaml
cat /tmp/crowdsec.yaml
rm /tmp/crowdsec.yaml
```