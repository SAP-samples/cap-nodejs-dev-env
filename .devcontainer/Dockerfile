# syntax=docker/dockerfile:1

ARG VARIANT="24"
FROM mcr.microsoft.com/devcontainers/javascript-node:${VARIANT}

# Add package info for cf CLI
# The upstream signing key expired 2020-09-12 and has not been rotated, so this
# repo is marked trusted (skips signature verification) rather than using signed-by.
RUN echo "deb [trusted=yes] https://packages.cloudfoundry.org/debian stable main" \
  | tee /etc/apt/sources.list.d/cloudfoundry-cli.list

# Install some generally useful tools, including cf CLI
RUN apt-get update \
  && apt-get -y install --no-install-recommends \
  cf8-cli \
  curl \
  entr \
  git \
  sqlite3 \
  watch \
  yq

# Install latest SAP CAP SDK globally
USER node
RUN npm install -g \
  @sap/cds-dk@latest

WORKDIR /home/node
