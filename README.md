# bacon-comp

## Requirements
* [npm-lnker](https://github.com/ostosh/npm-lnkr)
* [bulk](https://github.com/timoxley/bulk)

## How To Notes

###
1. clone bacon-comp
2. npm run setup-comp
3. cd path/to/submodule
4. execute any custom configurations/build steps for each submodule

### config
* git config --global diff.submodule log (so you get clearer container diffs when referenced submodule commits changed)
* git config --global fetch.recurseSubmodules on-demand (so you are confident new referenced commits for known submodules get fetched with container updates)
* git config --global status.submoduleSummary true (so git status gets useful again when a referenced submodule commit changed)

### Adding or cloning
* Initial add: git submodule add <url> <path>
* Initial container clone: git clone --recursive <url> [<path>]

### Grabbing updates inside a submodule
1. cd path/to/submodule
2. git fetch
3. git checkout -q <commit-sha1>
4. cd -
5. git commit -am “Updated submodule X to: blah blah”

### Grabbing container updates
1. git pull
2. git submodule sync --recursive
3. git submodule update --init --recursive

### Updating a submodule inside container code
1. git submodule update --remote --rebase -- path/to/module
2. cd path/to/submodule
3. local work, testing, eventually staging
4. git commit -am “Update to central submodule: blah blah”
5. git push
6. cd -
7. git commit -am “Updated submodule X to: blah blah”

### Permanently removing a submodule (1.7.8+)
1. git submodule deinit path/to/submodule
2. git rm path/to/submodule
3. git commit -am “Removed submodule X”

