## importing a new version

1. `../runbooks/import-upstream 3.11.0a1`  # comment out the branch part
2. do this for all of the releases:
    - `git checkout upstream -b ubuntu/focal`
    - copy the `debian` directory from the previous version
    - `git add debian && git commit -m '...'`
    - change the package versions in debian/*
    - *sometimes* you'll want to copy the patches from the closest nightly
    - `../runbooks/refresh-patches ubuntu/focal`
    - `dch -v ...`
    - `../runbooks/build` and adjust until successful
