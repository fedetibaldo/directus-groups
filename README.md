# Directus Groups

> &nbsp;
> A range of extensions to yield collection groups in Directus
> &nbsp;

## Installation

For development purposes, you can install the demo Directus application by following the [official Directus installation tutorial](https://docs.directus.io/installation/docker.html) using [Docker](https://www.docker.com/). The `docker-compose` file is already present in the root directory of the repository.

## Development

Make sure you're running [node](https://nodejs.org/dist/latest-v13.x/) version 13. If you are a [nvm](https://github.com/nvm-sh/nvm) user, run
```bash
nvm use # sets node to version 13
```

Install [Lerna](https://lerna.js.org/), if you haven't already.
```bash
npm i -g lerna
```

From the root of the project, install the required node modules.
```bash
lerna bootstrap
```

Next, run
```bash
docker-compose up -d # starts Directus
lerna run dev
```

Last but not least, enjoy!

## Copyright & License

This repository is licensed under the Apache License 2.0. Any sub package which fails to state otherwise, has to be considered as licensed under the same terms.
