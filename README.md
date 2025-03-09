Docker images for droidian
==========================

This repository contains the required source files to build Docker images
for various release engineering tasks (package building, hardware adaptation building, rootfs building, etc...).

These are built in Circle CI and, for the 'master' branch, the build artifacts are pushed automatically
into quay, at the [droidian organization](https://quay.io/repository/droidian/build-essential).

Currently built images
----------------------

* build-essential (amd64 and arm64)

Adding a new image template
---------------------------

Image templates must be stored in the root directory of this repository, and must be named as `Dockerfile.@template@.in`,
where `@template@` is the template name.

The following strings are replaced:

| String            | Description                            | Example (for `arm64/droidian/build-essential:trixie`) |
|-------------------|----------------------------------------|-------------------------------------------------------------|
| `%(target_name)s` | Sanitized slug of the full target name | `arm64_droidian_build_essential_trixie`                     |
| `%(arch)s`        | Architecture                           | `arm64`                                                     |
| `%(namespace)s`   | Docker namespace                       | `droidian`                                                  |
| `%(template)s`    | Template name                          | `build-essential`                                           |
| `%(tag)s`         | Image tag                              | `trixie`                                                    |
