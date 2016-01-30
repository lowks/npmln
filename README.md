##NPMLN - Symlink NPM Modules (Experimental)

install npmln
```
sudo pip install npmln
```

usage
```bash
npmln i                              # install dependencies and peerDependencies (./package.json)
npmln i --dev                        # install all including devDependencies (./package.json)
npmln i gulp grunt-cli typescript -g # install specific modules globally
```

supported formats in package.json are:
- name: version
- gzipped tarball url(http.\*?tar.gz)
- github urls (http.\*?.git, http.\*.git#branch)
- github (username/repo) version string
- npm's scoped modules (@scope/repo)

```
positional arguments:
  commands              npmln commands (install)

optional arguments:
  -h, --help            show this help message and exit
  -g                    symlink bin globally into (--prefix), with sudo
  --base BASE           base directory for install (.), lookup package.json
  --prefix PREFIX       global bin scripts will be installed into
                        (/usr/local)/bin/
  --pkg-dir PKG_DIR     Package directory to be installed (/var/tmp/npmln)
  --tmp-dir TMP_DIR     tmp folder to download gzipped tarballs (/dev/shm)
  --no-prod             don't install dependencies and peerDependencies
                        (False)
  --dev                 install devDependencies (False)
  --semver-patch        respect semver patch (False)
  --semver-minor        respect semver minor (False)
  --retries RETRIES     retries when url read failed (20)
  --reinstall           reinstall regardless of link exists (False)
  --allow-node-modules  allow node_modules folder to be included in package
                        (False)
  -v                    show program's version number and exit
```

#### Known issues
- does not work properly with package bundlers/transpilers/module loaders/plugin loaders,
that does not use normal require('...') and don't have sub packages in dependencies section of package.json
