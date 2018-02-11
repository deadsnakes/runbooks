## Import from an upstream .dsc

1. Find a suitable source, prefer the ubuntu packaging from some future lts.
1. `dget $url.dsc`
1. `gbp import-dsc --pristine-tar /path/to/pythonxx_x.x.x.dsc`
1. Push branches to origin:
   ```bash
    git checkout master && git push origin HEAD --tags
    git checkout pristine-tar && git push origin HEAD
    git checkout upstream && git push origin HEAD
    ```
1. Refresh patches so future diffs are easier to read
  ([see updating.md][refreshing-patches]).
1. Apply similar patches (if needed) as other packages.  [python3.6][python3.6]
   is usually a good place to look.

[refreshing-patches]: https://github.com/deadsnakes/runbooks/blob/master/updating.md#create-patch-queue-branch
[python3.6]: https://github.com/deadsnakes/python3.6/commits/master
