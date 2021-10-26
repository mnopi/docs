# GIT

### [bit](https://github.com/chriswalz/bit)
````bash
bit save [commit message]  # git commit -am "commit message"
bit sync  # git pull -r; git push
bit sync origin main  # git pull -r; git push; git pull -r origin master; git push
bit switch example-branch
````

### [git.io url](https://gist.github.com/dikiaap/01f5e2ba3c738012aef0a8f524a6e207)
```shell
FILE="rc"
curl https://git.io/ -i -F "url=https://raw.githubusercontent.com/j5pux/${FILE}/main/${FILE}" -F "code=_${FILE}"
```

### [git-extras](https://github.com/tj/git-extras/blob/master/Commands.md)

```shell
brew install git-extras
git extras --help
```

* [feature](https://github.com/tj/git-extras/blob/master/Commands.md#git-feature)
* [summary](https://github.com/tj/git-extras/blob/master/Commands.md#git-summary)
* [bulk](https://github.com/tj/git-extras/blob/master/Commands.md#git-bulk)
* [brv](https://github.com/tj/git-extras/blob/master/Commands.md#git-bulk)
* [force-clone](https://github.com/tj/git-extras/blob/master/Commands.md#git-force-clone)
* [release](https://github.com/tj/git-extras/blob/master/Commands.md#git-release)
* [rename-branch](https://github.com/tj/git-extras/blob/master/Commands.md#git-rename-branch)
* [rename-branch](https://github.com/tj/git-extras/blob/master/Commands.md#git-rename-branch)
* [rename-tag](https://github.com/tj/git-extras/blob/master/Commands.md#git-rename-tag)
* [rename-remote](https://github.com/tj/git-extras/blob/master/Commands.md#git-rename-remote)
* [alias](https://github.com/tj/git-extras/blob/master/Commands.md#git-alias)
* [info](https://github.com/tj/git-extras/blob/master/Commands.md#git-info)
* [cp](https://github.com/tj/git-extras/blob/master/Commands.md#git-cp)
* [create-branch](https://github.com/tj/git-extras/blob/master/Commands.md#git-create-branch) 
  `git create-branch -r origin development`
* [delete-branch](https://github.com/tj/git-extras/blob/master/Commands.md#git-delete-branch)
* [delete-submodule](https://github.com/tj/git-extras/blob/master/Commands.md#git-delete-submodule)
* [delete-tag](https://github.com/tj/git-extras/blob/master/Commands.md#git-delete-tag)
* [merge-into](https://github.com/tj/git-extras/blob/master/Commands.md#git-merge-into)
* [graft](https://github.com/tj/git-extras/blob/master/Commands.md#git-graft)
* [undo](https://github.com/tj/git-extras/blob/master/Commands.md#git-undo)
* [setup](https://github.com/tj/git-extras/blob/master/Commands.md#git-setup)
* [touch](https://github.com/tj/git-extras/blob/master/Commands.md#git-touch)
* [obliterate](https://github.com/tj/git-extras/blob/master/Commands.md#git-obliterate)
* [local-commits](https://github.com/tj/git-extras/blob/master/Commands.md#git-local-commits)
* [missing](https://github.com/tj/git-extras/blob/master/Commands.md#git-missing)
* [lock](https://github.com/tj/git-extras/blob/master/Commands.md#git-lock)
* [locked](https://github.com/tj/git-extras/blob/master/Commands.md#git-locked)
* [unlock](https://github.com/tj/git-extras/blob/master/Commands.md#git-unlock)
* [reset-file](https://github.com/tj/git-extras/blob/master/Commands.md#git-reset-file)
* [pr](https://github.com/tj/git-extras/blob/master/Commands.md#git-pr)
* [root](https://github.com/tj/git-extras/blob/master/Commands.md#git-pr)
* [delta](https://github.com/tj/git-extras/blob/master/Commands.md#git-delta)
* [sync](https://github.com/tj/git-extras/blob/master/Commands.md#git-sync)
  `git sync origin master`
* [browse](https://github.com/tj/git-extras/blob/master/Commands.md#git-browse)

## [pre-commit](https://pre-commit.com/)

### setup
````bash
grep -q "pre-commit" $(DIR).git/hooks/pre-commit 2>/dev/null \
|| [[ -f $(DIR).pre-commit-config.yaml ]] \
|| pre-commit sample-config > $(DIR).pre-commit-config.yaml \
&& pre-commit install --install-hooks && pre-commit autoupdate
````

### [Templates & Hooks](https://git-scm.com/docs/githooks)
````bash
git config --global init.templateDir 
for i in pre-commit pre-merge-commit pre-push prepare-commit-msg commit-msg post-commit post-checkout post-merge; do
  pre-commit init-templatedir $GIT/templates --hook-type $i 
done
````

### Develop 
[pip-tools](https://github.com/jazzband/pip-tools/blob/master/.pre-commit-hooks.yaml)
````bash
pre-commit sample-config
pre-commit install --install-hooks 
pre-commit autoupdate
````

## Commands
````bash
git rm --cached -r -f .  # remove all files from git index without removing files.
git ls-remote --heads origin
git branch -a --contains tags/v0.9.9
git rev-list origin..HEAD  # or git rev-list HEAD ^origin
git diff --name-only HEAD~10..HEAD install.d/usr/bin  # git files diff for 10 commits
````

* %(refname): refs/heads/main
* %(refname:short): main

````bash
$ git branch --all --format='%(refname:short)'  # all branches
: '
main
origin/main
'

````
### [Upstream branch](https://devconnected.com/how-to-set-upstream-branch-on-git/)
Branch tracked on remote repository by `local remote branch/remote tracking branch`.
When cloning or creating new feature branches, you will have to set upstream branches in order to work properly.
`local branch` -> `local remote branch/remote tracking branch` -> `remote repository tracked/upstream branch`.

````bash
git push -u origin HEAD  # the same as set upstream with same branch name.
git push -u origin master  # -u is --set-upstream.
git branch --track main origin/main  # seems to be the same if local main is not tracking remote main.
````

* `git fetch` updates remote branches locally: `origin/master` so it can have useful tracking info.
* `git pull `does `git fetch` and `git merge origin/master` (fetches to `local origin/master` and merges into `master`).
* `git merge origin/master` `git rebase origin/master`

### [Rebase vs. merge](https://sdqweb.ipd.kit.edu/wiki/Git_pull_--rebase_vs._--merge)
````bash
git pull --rebase  # local changes are reapplied on top of the remote changes.
git pull --rebase origin master  # similar to 'git fetch & git rebase'
git pull --merge   # (default) local changes are merged with the remote changes.
: '
This results in a merge commit that points to the latest local commit and the latest remote commit.
'
git pull origin master  # similar to 'git fetch & git merge'
: '
If branch is created in web and 
'
git fetch --all  # is now in local remotes but there is not a local which track remote.
````

## See also

### Actions - Examples
  * [critic.sh - Bash Test](https://github.com/Checksum/critic.sh/blob/master/.github/workflows/main.yml)

### GitHub
  * [gh pr](https://cli.github.com/manual/gh_pr_create) - gh pr create.
  * [Authentication in a workflow](https://docs.github.com/en/actions/reference/authentication-in-a-workflow)
  * [Encrypted secrets](https://docs.github.com/en/actions/reference/encrypted-secrets)
  * [Introduction to GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions)
  * [Manually running a workflow](https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow) 

### How-To
  * [create-custom-github-action](https://www.philschmid.de/create-custom-github-action-in-4-steps)
  * [Automate your build & release](https://faun.pub/automate-your-build-release-with-github-actions-367c0febf5fd)
  * [Automating PyPI releases](https://www.caktusgroup.com/blog/2021/02/11/automating-pypi-releases/)
  * [Publishing PyPI package distribution](https://packaging.python.org/guides/publishing-package-distribution-releases-using-github-actions-ci-cd-workflows/)
  * [Setting up python-semantic-release](https://python-semantic-release.readthedocs.io/en/latest/automatic-releases/github-actions.html)
  * [PyPI publish GitHub Action](https://github.com/pypa/gh-action-pypi-publish)
  * [Automate your build & release](https://faun.pub/automate-your-build-release-with-github-actions-367c0febf5fd)

