# bacon-comp

## Requirements
* [node/npm](https://nodejs.org/en/)
* [npm-lnker](https://github.com/ostosh/npm-lnkr)
* [bulk](https://github.com/timoxley/bulk)

## How To Notes

### Install
1. install node/npm
2. clone bacon-comp
3. npm install -g npm-lnkr bulk
4. npm run init-comp
5. npm run setup-comp
6. cd path/to/submodule
7. execute any custom configurations/build steps for each submodule

### Git Configuration
* git config --global diff.submodule log (so you get clearer container diffs when referenced submodule commits changed)
* git config --global fetch.recurseSubmodules on-demand (so you are confident new referenced commits for known submodules get fetched with container updates)
* git config --global status.submoduleSummary true (so git status gets useful again when a referenced submodule commit changed)

### Grabbing container updates
1. git pull
2. git submodule sync --recursive
3. git submodule update --init --recursive

### Adding a submodule
* Initial add: git submodule add <url> <path>

### Permanently removing a submodule
1. git submodule deinit path/to/submodule
2. git rm path/to/submodule
3. git commit -am “Removed submodule X”

### Grabbing updates/change branch from a submodule
1. cd path/to/submodule
2. git fetch
3. git checkout -q <commit-sha1>
4. cd -
5. git commit -am “Updated submodule X to: blah blah”

### Pushing updates to a submodule
1. git submodule update --remote --rebase -- path/to/module
2. cd path/to/submodule
3. local work, testing, eventually staging
4. git commit -am “Update to central submodule: blah blah”. WARNING: if committing to local head, checking out remote branch after this step will wipe locally committed (unpushed) changes. It is recommended that you instead work from a local branch when making changes to submodules
5. git push
6. cd -
7. git commit -am “Updated submodule X to: blah blah”
