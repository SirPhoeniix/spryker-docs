---
title: Integrating the Docker SDK into existing projects
description: The included instructions describe how to convert an existing non-docker based project into a docker based one.
originalLink: https://documentation.spryker.com/v6/docs/integrating-the-docker-sdk-into-existing-projects
originalArticleId: fad44eed-3775-47b8-9483-37a2a9419827
redirect_from:
  - /v6/docs/integrating-the-docker-sdk-into-existing-projects
  - /v6/docs/en/integrating-the-docker-sdk-into-existing-projects
---

This page describes how you can convert a non-Docker based project into a Docker based one. If you want to install Spryker in Docker from scratch, start with [Development Mode](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/installation-guides/choosing-an-installation-mode.html#development-mode) or [Demo Mode](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/installation-guides/choosing-an-installation-mode.html#demo-mode).

## Prerequisites

To start integrating Docker into your project:

1. Follow one of the Docker installation prerequisites:
    * [Installing Docker prerequisites on MacOS](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/docker-installation-prerequisites/installing-docker-prerequisites-on-macos.html)
    * [Installing Docker prerequisites on Linux](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/docker-installation-prerequisites/installing-docker-prerequisites-on-linux.html)
    * [Installing Docker prerequisites on Windows](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/docker-installation-prerequisites/installing-docker-prerequisites-on-windows.html)
2. Integrate the [Spryker Core](/docs/scos/dev/migration-and-integration/202009.0/feature-integration-guides/spryker-core-feature-integration.html) feature into your project. 

## Set up .dockerignore

Create a new `.dockerignore` file to match the project file structure:
```yaml
.git
.idea
node_modules
/vendor
/data
!/data/import
.git*
.unison*
/.nvmrc
/.scrutinizer.yml
/.travis.yml
/newrelic.ini

/docker
!/docker/deployment/
```
See [.dockerignore file](https://docs.docker.com/engine/reference/builder/#dockerignore-file) to learn more about the structure of the file.

## Set up configuration

In `config/Shared`, adjust or create a configuration file. The name of the file should correspond to your environment. See  [config_default-docker.php](https://github.com/spryker-shop/b2c-demo-shop/blob/master/config/Shared/config_default-docker.php) as an example. 

Make sure to adjust the configuration for each separate store. See [config_default-docker_DE.php](https://github.com/spryker-shop/b2c-demo-shop/blob/master/config/Shared/config_default-docker_DE.php) as an example.

## Set up a Deploy file

Set up a [Deploy file](/docs/scos/dev/developer-guides/202009.0/docker-sdk/deploy-file-reference-1.0.html) per your infruscturcure requirements using the examples in the table:

| Development mode | Demo mode |
| --- | --- |
| [B2C Demo Shop deploy file](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.dev.yml) | [B2C Demo Shop deploy file](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.yml) |
| [B2B Demo Shop deploy file](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.dev.yml) | [B2B Demo Shop deploy file](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.yml) |

## Set up the installation script

In `config/Shared`, prepare the installation recipe that defines the way Spryker should be installed.

Use the following recipe examples:
* [B2B Demo Shop installation recipe](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.yml)
* [B2C Demo Shop installation recipe](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.yml)

## Install the Docker SDK
Follow the steps to install the Docker SDK:
1. Fetch Docker SDK tools:
```bash
git clone https://github.com/spryker/docker-sdk.git ./docker
```
{% info_block warningBox "Verification" %}

Make sure `docker 18.09.1+` and `docker-compose 1.23+` are installed:

```bash
$ docker version
$ docker-compose --version
```

{% endinfo_block %}

2. Initialize docker setup:
 ```bash
docker/sdk bootstrap
```
{% info_block infoBox "Bootstrap" %}

Once you finish the setup, you don't need to run `bootstrap` to start the instance. Run it only after:
* Docker SDK version update
* Deploy file update

{% endinfo_block %}
3. Build and run Spryker applications:
```bash
docker/sdk up
```

{% info_block warningBox %}

Ensure that, in the `hosts` file in the local environment, all the domains from `deploy.yml` are defined as `127.0.0.1`.

{% endinfo_block %}


## Endpoints

To ensure that the installation is successful, make sure you can access the configured endpoints from the Deploy file. See [Deploy file reference - 1.0](/docs/scos/dev/developer-guides/202009.0/docker-sdk/deploy-file-reference-1.0.html) to learn about the Deploy file.

{% info_block infoBox "RabbitMQ UI credentials" %}

To access RabbitMQ UI, use `spryker` as a username and `secret` as a password. You can adjust the credentials in `deploy.yml`.

{% endinfo_block %}



## Getting the list of useful commands

To get the full and up-to-date list of commands, run `docker/sdk help`.

## Next steps
* [Troubleshooting](/docs/scos/dev/developer-guides/202009.0/troubleshooting/spryker-in-docker-issues/troubleshooting-docker-installation/docker-daemon-is-not-running.html)
* [Debugging Setup in Docker](/docs/scos/dev/developer-guides/202009.0/docker-sdk/configuring-debugging-in-docker.html)
* [Deploy File Reference - 1.0](/docs/scos/dev/developer-guides/202009.0/docker-sdk/deploy-file-reference-1.0.html) 
* [Services](/docs/scos/dev/developer-guides/202009.0/docker-sdk/configuring-services.html)
* [Self-signed SSL Certificate Setup](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/configuration/setting-up-a-self-signed-ssl-certificate.html) 
* [Additional DevOPS Guidelines](/docs/scos/dev/developer-guides/202009.0/installation/installing-spryker-with-docker/configuration/additional-devops-guidelines.html)
