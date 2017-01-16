# Docker image for Yarn

## Usage

### Build the image

```shell
git clone https://github.com/marcverney/marcv-yarn.git
cd marcv-yarn
docker build -t marcv/yarn .
```

### Run a Yarn command

#### Minimal command:

```shell
docker run -v `pwd`:/opt/app marcv/yarn [<yarn_command>]
```

Note: `yarn_command` is the full [yarn command](https://yarnpkg.com/en/docs/cli/), including all its arguments, but without the initial `yarn` keyword. If no `yarn_command` is provided, `yarn install` is run.

#### Example:

```shell
docker run --rm -t -v `pwd`:/opt/app -v ~/.cache:/root/.cache marcv/yarn install --prod
```

This example command uses the following additional arguments:

- `--rm` to clean up the container one the command has been executed
- `-t` to allocate a pseudo-tty to the container (colored output, etc.)
- `-v ~/.cache:/root/.cache` so that Yarn uses the host's current user's `.cache` directory (otherwise, the cache is lost when the container is destroyed)  