#ARG BUILD_FROM="alpine:latest"
ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

// build.json 
{
  "squash": false,
  "build_from": {
    "aarch64": "ghcr.io/hassio-addons/base/aarch64:11.0.0",
    "amd64": "ghcr.io/hassio-addons/base/amd64:11.0.0",
    "armhf": "ghcr.io/hassio-addons/base/armhf:11.0.0",
    "armv7": "ghcr.io/hassio-addons/base/armv7:11.0.0",
    "i386": "ghcr.io/hassio-addons/base/i386:11.0.0"
  },
  "args": {}
}

// package.json
{
  "name": "my_package",
  "description": "",
  "version": "1.0.0",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "mqtt": "^4.2.8",
    "serialport": "^9.2.8"
  },
  "homepage": "https://github.com/monatheoctocat/my_package"
}

# Install requirements for add-onRUN apk add --no-cache jq npm make gcc g++ python3 linux-headers udev

WORKDIR /
COPY package.json /
RUN npm install

WORKDIR /share

RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
