runbooks
========

Release lifecycle runbooks.

This is mostly for documenting how the development / release of deadsnakes
packages is done.


### building a `py#.##` repo

first materialize the repo / distribution you want to work on:

```bash
../runbooks/meta-gbp materialize noble
```

then call build

```bash
../runbooks/meta-gbp build
```

The output will be in `../dist`.


### adding a dockerfile for a new ubuntu release

Use the `./make-new-image` script to generate a dockerfile based on a
control file.  For example:

```bash
./make-new-image \
    --codename focal \
    ../python3.6/debian/control > dockerfiles/Dockerfile.focal
```
