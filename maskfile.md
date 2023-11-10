# Tasks for Japanese i18n support to Snap-Hutao-Docs

Using [mask](https://github.com/jacobdeichert/mask)

## patch

> Create a patch and copy it to windows

```bash
mask clean
mask diff-patch
mask copy2win-patch
```

## diff-patch

> Create a patch

```bash
PRODUCT_NAME="Snap-Hutao-Docs"
TODAY=$(date +'%Y%m%d')
BRANCH_NAME=$(git branch --show-current | sed -e "s/\//_/g")
REMOTE_NAME="origin"
DEFAULT_BRANCH="main"

if [[ "$BRANCH_NAME" = "$DEFAULT_BRANCH" ]] || [[ "$BRANCH_NAME" = "patch-"* ]]; then
    echo "This branch is "$DEFAULT_BRANCH" or patch branch"

    for p in "$PRODUCT_NAME" "." "$TODAY" "." "patch"; do
        PATCH_NAME+=$p
    done
else
    echo "This branch is uniq feat branch"

    for p in "$PRODUCT_NAME" "_" "$BRANCH_NAME" "." "$TODAY" "." "patch"; do
        PATCH_NAME+=$p
    done
fi

echo "patch file name: $PATCH_NAME"
git diff "$REMOTE_NAME/$DEFAULT_BRANCH" >"$PATCH_NAME"
```

## patch-branch

> Create a patch branch

```bash
TODAY=$(date +'%Y%m%d')
git switch -c "patch-$TODAY"
```

## switch-master

> Switch to master branch

```bash
DEFAULT_BRANCH="main"
git switch $DEFAULT_BRANCH
```

## delete-branch

> Delete patch branch

```bash
mask clean
mask switch-master
git branch --list "patch*" | xargs -n 1 git branch -D
```

## clean

> Run clean

```bash
rm -f ./*.patch
rm -f ./*.patch.gpg
rm -f ./*.zip
```

## copy2win-patch

> Copy patch to Windows

```bash
cp *.patch $WIN_HOME/Downloads/
```

## run

> Run local test

```bash
pnpm run docs:dev
```

## TODO

- [x] advanced/dependency.md
- [x] advanced/exceptions.md
- [ ] advanced/FAQ.md
- [ ] advanced/Gacha-system-and-export-principal.md
- [ ] advanced/get-stoken-cookie-from-the-third-party.md
- [ ] advanced/known-issue.md
- [ ] advanced/README.md
- [ ] advanced/uninstall.md
- [ ] community.md
- [ ] development/contribute.md
- [ ] development/platform.md
- [ ] development/README.md
- [ ] features/achievements.md
- [ ] features/character-data.md
- [ ] features/character-wiki.md
- [ ] features/dashboard.md
- [ ] features/develop-plan.md
- [ ] features/game-launcher.md
- [ ] features/hutao-API.md
- [ ] features/hutao-settings.md
- [ ] features/mhy-account-switch.md
- [ ] features/monster-wiki.md
- [ ] features/README.md
- [ ] features/real-time-notes.md
- [ ] features/setup.md
- [ ] features/weapon-wiki.md
- [ ] features/wish-export.md
- [ ] i18n.md
- [ ] menu.md
- [ ] project.md
- [ ] quick-start.md
- [ ] README.md
- [ ] side-load.md
- [ ] star-request.md
- [ ] statements/bug-report.md
- [ ] statements/privacy-notice.md
- [ ] statements/README.md
- [ ] statements/tos.md
- [ ] statements/update-log.md
