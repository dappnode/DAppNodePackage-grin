# DAppNodePackage-grin

[![DAppNodeStore Available](https://img.shields.io/badge/DAppNodeStore-Available-brightgreen.svg)](http://my.dappnode/#/installer/grin.dnp.dappnode.eth)

DAppNode package for the private and lightweight mimblewimble blockchain.

## How to use

This package is intended to be used as a daemon only. To use your wallet, you must run it separately and connect to the daemon as follows:

`grin-wallet -r "http://grin.dappnode:3413" info`

Check the project's [wiki](https://github.com/mimblewimble/docs/wiki/Wallet-User-Guide) for more information.

## Build Prerequisites

- git

  Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

  Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding current user to docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

  Install [docker-compose](https://docs.docker.com/compose/install)

## Building

`docker-compose build`

## License

This project is licensed under the Apache License v2.0 - see the [LICENSE](LICENSE) file for details
