runbooks
========

Release lifecycle runbooks.

This is mostly for documenting how the development / release of deadsnakes
packages is done.


### building a package

From the source directory (such as `python3.6`) run the `./build` script
included in this repository.  For instance:

```bash
../runbooks/build
```

`./build` will pick up on the codename specified in `debian/changes` and
build debian packages using `docker` or `podman`.

The output will be in `../dist`.


### adding a dockerfile for a new ubuntu release

Use the `./make-new-image` script to generate a dockerfile based on a
control file.  For example:

```bash
./make-new-image \
    --codename focal \
    ../python3.6/debian/control > dockerfiles/Dockerfile.focal
```
