## Update the upstream branch

1. `../runbooks/import-upstream <VERSION>`

## Create patch queue branch

1. `git checkout ubuntu/xenial`
1. `gbp pq import` This will create the patch-queue branch with the patches 1 commit per patch
1. `git checkout ubuntu/xenial`  Switch back so we can merge in upstream
1. `git merge upstream`
1. `gbp pq rebase`  Resolve any conflicts encountered here
1. `gbp pq export`  This will create new patch files on the original branch
1. `git add debian/patches && git commit -m "Refresh patches."`

## Verifying

1. `git checkout ubuntu/xenial`
1. `dch -v ...`
1. `git add -u && git commit -m ...`
1. `../runbooks/build`  Run the build!
1. If it fails, fix things by rebasing on the `Refresh patches.` commit.

## Uploading

1. `rm -rf ../dist`  Ensure the dist directory is gone from previous runs
1. `../runbooks/build --source` Build the source package
1. `cd ../dist && dput ppa:deadsnakes/ppa *.changes` Upload to launchpad
1. `git checkout master && git push origin HEAD`
1. `git checkout ubuntu/xenial`
1. `git tag ... && git push origin HEAD --tags`
