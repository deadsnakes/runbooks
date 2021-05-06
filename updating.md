## Update the upstream branch

1. `../runbooks/import-upstream <VERSION>`

## Pull in upstream changes

1. `../runbooks/refresh-patches ubuntu/focal`

## Verifying

1. `../runbooks/build`  Run the build!
    - to do a quick validation use `../runbooks/quick-test`
1. If it fails, fix things by rebasing on the `Update SVER to ...` commit.
    - if symbols need updating, use `../runbooks/fix-symbols`

## Uploading

1. `../runbooks/release`
