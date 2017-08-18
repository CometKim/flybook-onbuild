# What is Flybook?
[Flybook](https://flybook.js.org) is a static site generator for documentation.

# How to use this image?
Requirements
* Docker 17.06+ (for multi-stage build)
* package.json (See [here](https://flybook.js.org/basic/configuration.html))
* docs (See [here](https://flybook.js.org/basic/getting-started.html))

When you build from this image, Flaybook will generate static files to `/docs`.

Then you can use [multi-stage build](https://docs.docker.com/engine/userguide/eng-image/multistage-build) to create a lightweight image that publishes outputs without build environments.

See an example:
```Dockerfile
FROM CometKim/flybook-onbuild:latest AS build-env

FROM nginx:latest AS production-env
COPY --from=build-env /out /usr/share/nginx/html
```
