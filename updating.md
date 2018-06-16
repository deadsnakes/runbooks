## Update the upstream branch

1. `../runbooks/import-upstream <VERSION>`

## Pull in upstream changes

1. `../runbooks/refresh-patches ubuntu/xenial`

## Verifying

1. `../runbooks/build`  Run the build!
1. If it fails, fix things by rebasing on the `Update SVER to ...` commit.

## Uploading

1. `rm -rf ../dist`  Ensure the dist directory is gone from previous runs
1. `../runbooks/build --source` Build the source package
1. `cd ../dist && dput ppa:deadsnakes/ppa *.changes` Upload to launchpad
1. `git checkout ubuntu/xenial`
1. `git tag ... && git push origin HEAD --tags`
