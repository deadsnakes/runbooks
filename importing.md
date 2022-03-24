## Import from an upstream .dsc

1. Find a suitable source, prefer the ubuntu packaging from some future lts.
1. `git init pythonx.x && cd pythonx.x`
1. `../runbooks/import-dsc $url.dsc`
1. Push branches to origin:
   ```bash
    git push origin ubuntu/bionic pristine-tar upstream --tags
    ```
1. Apply similar patches (if needed) as other packages.  [python3.6][python3.6]
   is usually a good place to look.

[python3.6]: https://github.com/deadsnakes/python3.6/commits/ubuntu/trusty
