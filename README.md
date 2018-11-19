# iac-prototype
IAC prototype - only used to report issue with docker-maven-plugin

Issue: https://github.com/fabric8io/docker-maven-plugin/issues/1124


This project is a proof-of-concept implementation/exploration of using Infrastructure-As-Code
in integration tests. Specifically I want to explore three possibilities:

1. A pure docker solution. Every set of integration tests requires a separate Dockerfile.

2. A pure ansible solution. There will be a single docker image with just enough installed
so it can be used as an ansible target. (To be specific that means python and SSH). Each
set of integration tests will use ansible to install the server and configure it.

3. A hybrid solution where we have a default configuration for each server (e.g, one for
mysql community, one for maria, one for postgresql 10, one for postgresql 11, etc.) Each
set of unit tests will use ansible to configure the server as required. That could mean
changing authentication mechanisms, prepopulating the test data, etc.

