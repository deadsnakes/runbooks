## new lts

1. (deadsnakes/runbooks) create new `Dockerfile` for the release

   for example:

   ```bash
   ./make-new-image --codename resolute ../py3.11/work/debian/control | tee dockerfiles/Dockerfile.resolute
   ```

   then **commit and push**

1. for each `py#.#` (that still successfully builds)

    if there are commits past `mainline` on the default branch create a
    backport branch
    - (often from `git log -1 --format=%H -- changelogs/mainline`)
    - merge back to `main` when done

    perform the following steps

    1. create new `debiandirs/<codename>`
       (often `cd debiandirs; ln -s $prev $codename`)
    1. create new `changelogs/{mainline,nightly}/<codename>`
       (often `cp changelogs/mainline/{$prev,$codename}`)
       (sometimes `cp changelogs/nightly/{$prev,$codename}`)
    1. bump version in changelog
       - `../runbooks/meta-gbp changelog --only $codename -m 'rebuild for $codename'`
    1. make sure it builds!
       - `../runbooks/meta-gbp materialize $codename`
       - `../runbooks/meta-gbp build`
    1. upload it!
       - `../runbooks/meta-gbp build --source`
       - `../runbooks/meta-gbp upload`
