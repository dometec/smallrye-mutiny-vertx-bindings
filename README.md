# SmallRye Reactive Utilities

[![Build Status](https://github.com/smallrye/smallrye-reactive-utils/workflows/SmallRye%20Build/badge.svg?branch=main)]( https://github.com/smallrye/smallrye-reactive-utils/actions?query=workflow%3A%22SmallRye+Build%22)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=smallrye_smallrye-reactive-utils&metric=alert_status)](https://sonarcloud.io/dashboard?id=smallrye_smallrye-reactive-utils)
[![License](https://img.shields.io/github/license/smallrye/smallrye-fault-tolerance.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Maven](https://img.shields.io/maven-central/v/io.smallrye.reactive/smallrye-reactive-utilities-projects?color=green)]()

This contains a set of modules helping the development of reactive applications in SmallRye 

## Vert.x Mutiny Clients

[Mutiny](https://smallrye.io/smallrye-mutiny) is a novel approach to deal with Reactive APIs.
The `vertx-mutiny-clients` module contains the Vert.x client API using the Mutiny model (`Uni` and `Multi`).

It also contains the Vert.x code generator.

## Reactive Converters

Reactive converters are a set of library to convert types uses by various libraries from/to `Publisher` and `CompletionStage`.
Documentation is available in [the reactive-converters directory](./reactive-converters/readme.adoc).

## Build

`mvn clean install`

## Release

- open a pull request updating the `.github/project.yml` file with the desired release version and next development version.
- once the pull request is merged, the release will be cut (tag, deployment...)

**IMPORTANT**: After the release, you must deploy the Javadoc:

1. checkout the created tag (`$VERSION`)
2. run `mvn javadoc:aggregate -DskipTests`
3. clone the website: `cd target  && git clone git@github.com:smallrye/smallrye-reactive-utils.git gh-pages  && cd gh-pages && git checkout gh-pages`
4. create a repository with the version name: `mkdir apidocs/$VERSION`
5. copy the generated content into the new directory `cp -R ../site/apidocs/* apidocs/$VERSION`
6. commit and push: `git add -A  && git commit -am "Publish javadoc for version $VERSION" && git push origin gh-pages`

