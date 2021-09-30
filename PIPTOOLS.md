# piptools

````makefile
all: vars clean
.PHONY: build bump clean pip-compile pip-compile-upgrade pip-sync pip-sync-upgrade pre-commit-setup publish test \
vars venv
BUMP := minor
SHELL := $(shell command -v bash)
DIR := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))
LATEST_TAG := $(shell git -C $(DIR) describe --tags --abbrev=0 2>/dev/null || { git tag v0.0.1 && echo v0.0.1; })
NAME := $(shell basename $(DIR))
PYTHON := $(shell which python3.9)
REQUIREMENTS := $(DIR)requirements
VENV := $(DIR)venv
ACTIVATE := $(VENV)/bin/activate

build: clean test
	@source $(ACTIVATE) && python3.9 -m build --sdist --wheel --no-isolation $(DIR)

bump: build
	git -C $(DIR)describe --abbrev=0 --tags 2>/dev/null || git tag v0.0.1
	cd $(DIR) && git -C  v tag "v$$( bump2version --dry-run --allow-dirty --current-version="$$( \
git -C $(DIR) tag --sort=taggerdate | tail -1 | sed 's/v//')" --list $(BUMP) | sed '/new_version/s/new_version=//' )"
	git -C $(DIR) tag --sort=taggerdate | tail -1
	git -C $(DIR)push --quiet --tags

clean:
	@rm -rf $(DIR)build
	@rm -rf $(DIR)/dist
	@rm -rf $(DIR)/*.egg-info

install:
	@python3.9 -m pip install -q --upgrade $(NAME)

pip-compile: venv
	@mkdir -p $(REQUIREMENTS) && cd $(REQUIREMENTS) && source $(ACTIVATE) && \
( \
pip-compile -q --no-annotate --allow-unsafe --rebuild --output-file requirements.txt $(DIR)setup.cfg; \
pip-compile -q --extra dev --no-annotate --allow-unsafe --rebuild --output-file requirements_dev.txt $(DIR)setup.cfg \
)

pip-compile-upgrade: venv
	@mkdir -p $(REQUIREMENTS) && cd $(REQUIREMENTS) && source $(ACTIVATE) && \
( \
pip-compile -q -U --no-annotate --allow-unsafe --rebuild --output-file requirements.txt $(DIR)setup.cfg; \
pip-compile -q -U --extra dev --no-annotate --allow-unsafe --rebuild --output-file requirements_dev.txt $(DIR)setup.cfg\
)

pip-sync: pip-compile
	@cd $(REQUIREMENTS) && pip-sync --python-executable sync -q requirements_dev.txt requirements.txt

pip-sync-upgrade: pip-compile-upgrade pip-sync

pre-commit-setup:
	@grep -q "pre-commit" $(DIR).git/hooks/pre-commit 2>/dev/null \
|| [[ -f $(DIR).pre-commit-config.yaml ]] \
|| pre-commit sample-config > $(DIR).pre-commit-config.yaml \
&& pre-commit install --install-hooks && pre-commit autoupdate

publish: bump
	@cd $(DIR) && twine upload -r user dist/* && make clean

test:
	@cd $(DIR) && source $(ACTIVATE) && pytest

vars:
	@echo "ACTIVATE: $(ACTIVATE)"
	@echo "DIR: $(DIR)"
	@echo "NAME: $(NAME)"
	@echo "LATEST_TAG: $(LATEST_TAG)"
	@echo "PYTHON: $(PYTHON)"
	@echo "REQUIREMENTS: $(REQUIREMENTS)"
	@echo "VENV: $(VENV)"

venv:
	@test -d $(VENV) || python3.9 -m venv $(VENV)
	@source $(ACTIVATE) && python -m pip install --upgrade -q pip setuptools wheel

````
## [py-compile](https://github.com/jazzband/pip-tools)
````bash
pip-compile -q --extra dev --extra test --no-annotate --allow-unsafe --rebuild --output-file requirements_dev.in \
  setup.cfg
pip-compile -q --no-annotate --allow-unsafe --rebuild --output-file requirements.in setup.cfg
pip-compile --extra beta --no-build-isolation --generate-hashes setup.cfg
pip-compile --extra beta --no-build-isolation --generate-hashes setup.cfg
pip-compile --extra dev --extra test  --upgrade --rebuild --no-build-isolation --generate-hashes \
  --output-file setup.cfg --output-file requirements_dev.in setup.cfg
pip-compile --strip-extras requirements_dev.in
````

