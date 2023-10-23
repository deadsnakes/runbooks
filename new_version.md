## importing a new version

0. `git commit --allow-empty -m 'empty initial commit'`
0. `git checkout -b upstream`
0. `git checkout main`
0. `../runbooks/import-upstream 3.11.0a1`  # comment out the branch part
0. do this for all of the releases:
    - `git checkout upstream -b ubuntu/focal`
    - copy the `debian` directory from the previous version
    - `git add debian && git commit -m '...'`
    - change the package versions in debian/*
    - *sometimes* you'll want to copy the patches from the closest nightly
    - `../runbooks/refresh-patches ubuntu/focal`
    - `dch -v ...`
    - `../runbooks/build` and adjust until successful
