## new nightly

1. create repository
    - add org secrets to repository
    - add repo to automation team with `Write` permission
1. copy `main` branch from previous nightly

   ```bash
   git remote add prev ../py3.14
   git fetch prev
   # actually maybe try and find the earliest beta1 commit?
   git reset --hard prev/main
   ```

1. replace versions
    - `README.md`
    - change the cpython submodule to be on the mainline

      ```bash
      # actually maybe try and find the first commit after the fork?
      git -C cpython checkout origin/main^ && git add cpython
      ```
    - changelogs (make sure to update package name too!)
        - force version to `3.##.0~a0-1+jammy1` for example

          ```bash
          find changelogs -type f |
            cut -d/ -f2- |
            xargs --replace bash -c '
                dist=$(cut -d/ -f2 <<< {});
                dch -v "3.15.0~a0-1+${dist}1" \
                    --package python3.15 \
                    -c changelogs/{} \
                    --force-distribution \
                    --distribution "$dist" \
                    "bump changelog"
                '
          ```

    - `control` / `rules` files

    - sometimes you'll have to edit the `relax-autoconf-version` patch due to
      conflicts :'(
1. push all the things!
