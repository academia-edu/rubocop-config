# linting-config

## Motivation

This repo is for linting configuration files that we want to share across multiple repositories. The reasoning is that what's sauce for the goose is sauce for the gander—if we use a linting rule in one repository, we should probably use it in other repositories too. Of course, idiosyncratic configuration (such as telling the linter what files to ignore) should usually go in the repository-specific configuration files.

## Rubocop

`academia-app/.rubocop.yml` uses `inherit_from` to load `linting-config/rubocop.yml` from GitHub. (This works because `linting-config` is a public repository.)

### Upgrading Rubocop

New versions of Rubocop often rename or remove cops, which means that old configuration files are often incompatible with new versions of Rubocop. This can cause Rubocop not to work if you're using [Rubocop Daemon](https://github.com/fohte/rubocop-daemon) (used by default in `academia-app`), since it'll continue running the version of Rubocop that's in the `Gemfile.lock` of whatever branch you started it in. You can work around this by restarting Rubocop Daemon, but that's a lot to ask of people who are just trying to commit. A better option is to disable Rubocop Daemon in advance of the upgrade, then re-enable it a few weeks later, once people aren't moving between new and old branches as much.
