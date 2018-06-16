## Update the upstream branch

1. `../runbooks/import-upstream <VERSION>`

## Pull in upstream changes

1. `../runbooks/refresh-patches ubuntu/xenial`

## Verifying

1. `../runbooks/build`  Run the build!
1. If it fails, fix things by rebasing on the `Update SVER to ...` commit.

## Uploading

1. `../runbooks/release`
