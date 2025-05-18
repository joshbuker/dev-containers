# dev-containers

Default dev container configs for quickly adding dev container support to a new project.

## Location

Place these files within a `.devcontainer` folder at the root level of your project (the level where you'll be opening VS Code).

## Available features

https://containers.dev/features

Add with:

```json
"features": {
  "<feature_goes_here>": {
    "version": "latest"
  }
}
```

## `.env` configuration

Add the following to your `devcontainer.json` file:

```json
// Set the environment variables
"runArgs": ["--env-file",".env"],
```

Or if you're using docker-compose, add the following under `app:`:

```yaml
env_file:
  - ../.env
```

This will use the `.env` file in your project root for importing env variables.

## mounting a local folder

For example, to map `~/linux` on the host to `/linux/kernel` on the container:

```json
// Mount ~/linux to /linux/kernel
"mounts": [
  "source=${localEnv:HOME}${localEnv:USERPROFILE}/linux,target=/linux/kernel,type=bind,consistency=cached"
],
```

Or map from the project root:

```json
"mounts": [
  "source=${localWorkspaceFolder}/.config/.wrangler,target=/home/node/.config/.wrangler,type=bind,consistency=cached"
],
```

## Install an apt dependency

Some applications may require a dependency such as `imagemagick`. Add the following to the Dockerfile, replacing `imagemagick` with your required dependencies:

```Dockerfile
RUN apt-get update && apt-get install -y imagemagick
```
