# Universal Messaging 10.11 example 1

## Prerequisites

- In [DockerHub](https://hub.docker.com/_/softwareag-universalmessaging-server) ensure you may pull `store/softwareag/universalmessaging-server:10.11`. Go to checkout and fill the information.
- On the machine running docker-compose execute `docker login` with the user that you used at the first step.

## Execution commands

```sh
# Start the server
docker-compose up
# or 
docker-compose up -d

# Stop the server, maintaining the volumes
docker-compose down

# Stop the server, destroying the volumes
docker-compose down -v
```

## Expected outcome

Four volumes are created at the first start (example from docker-desktop on Windows with WSL2):

```pwsh
PS Microsoft.PowerShell.Core\FileSystem::\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes> ls | findstr 'um-1011-example1'
d-----        2022-02-15     19:57                um-1011-example1_data
d-----        2022-02-15     19:57                um-1011-example1_temp
d-----        2022-02-15     19:57                um-1011-example1_license
d-----        2022-02-15     19:57                um-1011-example1_config
d-----        2022-02-15     19:57                um-1011-example1_logs
```

The volumes `um-1011-example1_license` and `um-1011-example1_config` now contain examples on how to pass the necessary configuration, i.e. your license and your user definition.

## Other references

- [Tech community UM container article](https://tech.forums.softwareag.com/t/universal-messaging-as-a-docker-container/254169)
- [users.txt file reference](https://documentation.softwareag.com/universal_messaging/num10-11/10-11_UM_webhelp/index.html#page/um-webhelp%2Fcce.um.users.configuration.html)
- [How to create users passwords](https://documentation.softwareag.com/universal_messaging/num10-11/10-11_UM_webhelp/index.html#page/um-webhelp%2Fco-jaas_auth_with_sin_4.html)

## Advanced

**Q: How can you know what folders to mount?**

A: execute `docker image inspect store/softwareag/universalmessaging-server:10.11` and look at the volumes section:

```bash
#...
  "Volumes": {
      "/opt/softwareag/UniversalMessaging/server/umserver/data": {},
      "/opt/softwareag/UniversalMessaging/server/umserver/licence": {},
      "/opt/softwareag/UniversalMessaging/server/umserver/logs": {},
      "/opt/softwareag/common/conf": {}
  },
#...
```
