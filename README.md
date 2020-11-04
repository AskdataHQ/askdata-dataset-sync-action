# Twine upload
## Usage
**Don't forget!** Set up `token` [secret](https://developer.github.com/actions/managing-workflows/storing-secrets/) for the Askdata Dataset Secret
```
name: Upload python to twine

on:
  push:
    branches:
    - master
    - releases/*

jobs:
  webhook:
    runs-on: ubuntu-latest
    steps:
    - uses: yaananth/twine-upload@v1
      env:
        RUNNER: ${{ toJson(runner) }}
        SECRETS: ${{ toJson(secrets) }}

```

This Github Action syncrhonize an Askdata dataset (More info [https://www.askdata.com])

# Contributing
## Creating tag
```
git checkout -b releases/v1
rm -rf node_modules
sed -i '/node_modules/d' .gitignore # Bash command that removes node_modules from .gitignore
git add node_modules .gitignore
git commit -am node_modules
git push origin releases/v1
git push origin :refs/tags/v1
git tag -fa v1 -m "Update v1 tag"
git push origin v1
```
## Updating tag
```
git checkout tags/v1 -b testtv1
npm run build
git commit -am "update"
git tag -fa v1 -m "Update v1 tag"
git push origin v1 --force
```

## Resources

See the walkthrough located [here](https://github.com/actions/toolkit/blob/master/docs/javascript-action.md) and versioning [here](https://github.com/actions/toolkit/blob/master/docs/action-versioning.md).
