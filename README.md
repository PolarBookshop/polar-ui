# Polar UI

This application is part of the Polar Bookshop system and provides the frontend functionality. It's part of the project built in the [Cloud Native Spring in Action](https://www.manning.com/books/cloud-native-spring-in-action) book by [Thomas Vitale](https://www.thomasvitale.com).

## Instructions

Run the following command to build the project.

```shell
./gradlew buildAngular
```

Then, package it in an NGINX container using the [pack](https://buildpacks.io/docs/tools/pack/) CLI and the Paketo Buildpacks.

```shell
pack build polar-ui \
  --buildpack gcr.io/paketo-buildpacks/nginx \
  --builder paketobuildpacks/builder:base \
  -p dist
```

Finally, you can run the container as follows.

```shell
docker run -d --name polar-ui --publish 9004:9004 --env PORT=9004 polar-ui
```
