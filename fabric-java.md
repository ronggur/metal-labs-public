---
title: fabric-java
excerpt: Experimental Fabric SDK for Java generated from OpenAPI Spec
slug: fabric-java
categories: [API]
type: [SDKs]
image: images/Experimental-Fabric-SDK-for-Java-generated-from-OpenAPI-Spec.jpg
social_image: images/share/Experimental-Fabric-SDK-for-Java-generated-from-OpenAPI-Spec_share.jpg
---

[![Experimental](https://img.shields.io/badge/Stability-Experimental-red.svg)](https://github.com/equinix-labs/equinix-labs/blob/main/uniform-standards.md)

> **[Experimental](https://github.com/equinix-labs/equinix-labs/blob/main/experimental-statement.md)**
> Vestibulum id ligula porta felis euismod semper. Maecenas faucibus mollis interdum. Cras justo odio, dapibus ac facilisis in, egestas eget quam.

## Prerequisite

This page has been updated @ May 31 2023

1. Jq (<https://stedolan.github.io/jq/>) : Jq command is used inside makefile to format OAS 3.0 json read from equinix public url.

   ```
    brew install jq
   ```

2. Docker : We can generate fabric-java client in two ways (described in later section), first is via utilising swagger codegen image to consume fabric OAS 3.0 spec which is provided as option in makefile. To install docker refer : <https://docs.docker.com/engine/install/>.

3. Building the API client library requires:
   1. Java 1.7+
   2. Maven

## Running sample

Build generated client:

```
cd equinix-openapi-fabric
mvn clean package
```

Aenean lacinia bibendum nulla sed consectetur. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum:

```
cd ..
java -classpath "equinix-openapi-fabric/target/equinix-openapi-fabric-1.0.0.jar:equinix-openapi-fabric/target/lib/*" your-example.java
```

## Generate and build equinix fabric java client

Maecenas faucibus mollis interdum. Aenean lacinia bibendum nulla sed consectetur :

```
make docker_run
```

Note : Etiam porta sem malesuada magna mollis euismod.

## Contribution guidelines

### Patching oas3.0 spec

1. Make changes in ``spec/oas3.patched.json`` dir.
2. Create a patch file in fabric-java:

   ```
   cd spec
   git diff oas3.patched/ > ../patches/spec.fetched.json/<patchfilename>
   cd ..
   ```

3. ``patchfilename`` should be in format: ``<patch_index>-<short_patch_decription_or_identifier>.patch``
4. Run ``make docker_run`` to reapply the changes to oas spec.
5. Before pushing changes, commit ``fabric-java/spec/oas3.patched.json`` along with the patch file.
