# Building extensions

Building extensions rely on the [tooling provided in the official buildpack](https://github.com/heroku/heroku-buildpack-php/blob/master/support/build/README.md).

We only support building in the Docker-based system, not in a dyno, so you will need Docker as well.

## Build environment setup

First, you need to initialize the submodule to get access to the buildpack tooling:

```bash
$ git submodule update --init
```

Then, you need to build the Docker environment. This must run from the root of the heroku-php-exts repository:

```bash
$ docker build --tag heroku-php-exts-cedar-14 --file $(pwd)/buildpack/support/build/_docker/cedar-14.Dockerfile .
```

**You will need to rebuild the image after each change to the formulae.** It will be fast thanks to the Docker layer cache.

You can then use the image to run your build environment. We provide an `env.default` file with the default config for the image. You will still need to provide the AWS credentials.

```bash
$ docker run --tty --interactive --env-file=support/build/_docker/env.default -e AWS_ACCESS_KEY_ID=... -e AWS_SECRET_ACCESS_KEY=... heroku-php-exts-cedar-14 /bin/bash
```

You then have a shell where you can run `bob build`, `buildpack/support/build/_util/deploy.sh` and so forth.
