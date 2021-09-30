#pre-commit

## setup
````bash
git config --global init.templateDir $GIT/templates
pre-commit init-templatedir $GIT/templates
  grep -q "pre-commit" $(DIR).git/hooks/pre-commit 2>/dev/null \
|| [[ -f $(DIR).pre-commit-config.yaml ]] \
|| pre-commit sample-config > $(DIR).pre-commit-config.yaml \
&& pre-commit install --install-hooks && pre-commit autoupdate
````
