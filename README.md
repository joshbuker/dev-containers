# dev-containers
Default dev container configs for quickly adding dev container support to a new project.

## `.env` configuration

Add the following to your `devcontainer.json` file:

```json
// Set the environment variables
"runArgs": ["--env-file",".env"],
```

This will use the `.env` file in your project root for importing env variables.
