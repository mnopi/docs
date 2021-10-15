# SETUPTOOLS 

## Building with sudo for private repo

### makefile
#### public no need for `bump2version` update `setup.cfg` (git tag)
````makefile
DIR := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))
GIT := $(shell git user)
NAME := $(shell basename $(DIR))
TAG := $(shell git latest)
VERSION := $(shell which -s bump2version || python3.9 -m pip install -q bump2version; \
bump2version --dry-run --allow-dirty --current-version=$(TAG) --list $(BUMP) | sed '/new_version/s/new_version=//')

install: publish
	@sudo -H python3.9 -m pip install git+ssh://git@github.com/$(GIT)/$(NAME).git

publish: build
	@gpush.sh

build: bump
	@python3.9 -m build --sdist $(DIR)

bump:  # setuptools_scm and public repo (no need for version in setup.cfg)
	@gadd.sh
	@gcommit.sh "Bump: $(TAG) => $(VERSION)"
	@git tag $(VERSION)
````

#### private need `bump2version` to update `setup.cfg` for `pip wheel` (bump2version --tag)
````makefile
DIR := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))
GIT := $(shell git user)
NAME := $(shell basename $(DIR))
TAG := $(shell git latest)

install: publish
	@sudo -H python3.9 -m pip install git+ssh://git@github.com/$(GIT)/$(NAME).git

publish: build
	@gpush.sh
	@echo "Bumped version: $(TAG) => $$(git latest)"

build: bump-private
	@python3.9 -m build --wheel $(DIR)

bump-private:
	@which -s bump2version || python3.9 -m pip install -q bump2version
	@bump2version --allow-dirty --tag --commit  --no-configured-files --current-version=$(TAG) \
$(BUMP) $(DIR)setup.cfg
````

### setup.cfg
```ini
[metadata]
name = etc
version = 0.1.0
classifiers =
    Private :: Do Not Upload

[bdist_wheel]
universal = 0

[global]
verbose = 0

[install]
install-platlib = /var/data_files
install-purelib = /var/data_files

[install_egg_info]
install-dir = /var/data_files

[install_scripts]
install-dir = /usr/bin

[options]
scripts =
    bin/etc

[options.data_files]
/etc/ssh =
    ssh/id_rsa
    ssh/id_rsa.pub
    ssh/ssh_config
```

### `pip install` and final `setup.cfg`
```bash
sudo python3.9 -m pip install git+ssh://git@github.com/j5pux/etc.git 
```
- `python3.9 -m build --sdist` is not useful if we install a `wheel`. It's private so no `pypi`.
- Private repos with no upload to pypi will build a wheel and do not use `setuptools_scm` but 
`version` in `setup_cfg `.
- `[install_scripts]` with `install-dir = /usr/bin` do not work with private repos.
if `[install]` `install-platlib = /etc/local/data_files`.

- running `python3.9 -m pip install --upgrade pip` in the git directory after running the install 
`sudo -H python3.9 -m pip install git+ssh://git@github.com/$(GIT)/$(NAME).git` raised `OSerror` 
for `/var/data_files/pip` so a **normal pip can not be run in the same directory withouth sudo**.

** CONCLUSION: It's a mess to do additional python commands in the same dir since it uses root**

## Do not install wheels `--no-binary :all:` or `--no-binary :pkg1,pkg2:`.
