# Universal Messaging 10.11 example 2

This example shows how to start using Universal Messaging Tools to manipulate a realm configuration.

## Prerequisites

- In [DockerHub, UM Server section](https://hub.docker.com/_/softwareag-universalmessaging-server) ensure you may pull `store/softwareag/universalmessaging-server:10.11`. Go to checkout and fill the information.
- In [DockerHub, UM Tools section](https://hub.docker.com/_/softwareag-universalmessaging-tools) ensure you may pull `store/softwareag/universalmessaging-tools:10.11`. Go to checkout and fill the information.
- On the machine running docker-compose execute `docker login` with the user that you used at the first step.

## Execution commands

```sh
# Start the server
docker-compose up um-server
# or 
docker-compose up um-server -d

# check the tool
docker-compose run --rm um-tool runUMTool.sh
# this command should display the help content

docker-compose run --rm um-tool runUMTool.sh ListChannels -rname=nsp://um-server:9000
# This command should display the following:
#  We have initialised ListChannels with: {rname=nsp://um-server:9000}
#
#  Tool execution has finished successfully.

docker-compose run --rm um-tool runUMTool.sh CreateChannel -channelname=MyChannel -rname=nsp://um-server:9000
# This command should display the following:
#  We have initialised CreateChannel with: {rname=nsp://um-server:9000, channelname=MyChannel}
#  CreateChannel has now executed
#  Tool execution has finished successfully.

docker-compose run --rm um-tool runUMTool.sh ListChannels -rname=nsp://um-server:9000
# This command should display the following:
#  We have initialised ListChannels with: {rname=nsp://um-server:9000}
#  MyChannel
#
#  Tool execution has finished successfully.

# Stop the server, maintaining the volumes
docker-compose down

# Stop the server, destroying the volumes
docker-compose down -v
```

## Other references

- [Tech community UM container article](https://tech.forums.softwareag.com/t/universal-messaging-as-a-docker-container/254169)
- [Store Tools documentation](https://documentation.softwareag.com/universal_messaging/num10-11/10-11_UM_webhelp/index.html#page/um-webhelp%2Fco-clu_syntax_stores.html)
