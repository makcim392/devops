# Description

This is a next.js app that is used to showcase docker and devops workflows.



# Running the next.js app

```bash
yarn run start
````

# Docker - containers

## Build the image (Colima) with legacy docker command

```bash
docker --context colima build -t api-rocket .
```

## Build the image (Colima) with buildx

Steps to Integrate Buildx
1. Ensure Buildx is Available to Docker

The docker-buildx command indicates the standalone executable is installed, but Docker doesn't recognize it as a CLI plugin. To resolve this:

Move the docker-buildx binary to the Docker CLI plugins directory:

mkdir -p ~/.docker/cli-plugins
ln -s $(which docker-buildx) ~/.docker/cli-plugins/docker-buildx

This command creates a symlink so Docker recognizes Buildx as a plugin.
2. Verify Buildx Integration

Run:

docker buildx version

You should now see version information for Buildx, indicating it's properly integrated.
3. Create a Buildx Builder

If this is the first time you're using Buildx, create a builder:

docker buildx create --use

To verify:

docker buildx ls

You should see a list of builders, with one marked as default.
4. Test Buildx

Now you can try your Buildx command again:

docker buildx build --tag api-rocket --load .

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t api-rocket --push .
```

