## new nightly

1. create repository
    - add org secrets to repository
    - add repo to nightly team
1. copy `main` branch from previous nightly
1. replace versions
    - `README.md`
    - changelogs (make sure to update package name too!)
        - force version to `3.##.0~a0-1+jammy1` for example
    - `control` / `rules` files
1. push all the things!
