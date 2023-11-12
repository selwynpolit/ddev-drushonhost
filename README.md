[![tests](https://github.com/rfay/ddev-drushonhost/actions/workflows/tests.yml/badge.svg)](https://github.com/rfay/ddev-drushonhost/actions/workflows/tests.yml) ![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

## What is ddev-drushonhost?

In DDEV v1.22.4+, the former facility to use the Drupal `drush` command on the host was removed.  That usage was always fragile, but some people liked and used it. Some also appreciate the performance gains this yields.  This also permits running PHPUnit/DTT ([Drupal Test Traits](https://gitlab.com/weitzman/drupal-test-traits)) tests on the host at higher speeds than running them in the containers. [See this article for more on running DTT on the host](https://selwynpolit.github.io/d9book/dtt#run-tests-on-the-host)

This add-on adds that facility again.

One-time in project:

`ddev get rfay/ddev-drushonhost`

When using drush on the host you need:

```
export IS_DDEV_PROJECT=true
```
or this in your `settings.local.php`:

```
putenv("IS_DDEV_PROJECT=true");
```

You may experience significant performance gains for `drush` commands when using this add-in.  [Read more about installing Global Drush and using this add-in](https://selwynpolit.github.io/d9book/drush#global-drush). Note. The host drush version doesn't matter much since it is only used to find the proper `drush` (most likely within /vendor/bin) and call it. This means you always run the version of `drush` that you installed in your project using composer.

From the former documentation:

**Warning:** We don’t recommend using `drush` on your host machine. It’s also mostly irrelevant for Drupal 9+, as you should be using Composer-installed, project-level `drush`.

If you have PHP and Drush installed on your host system and the environment variable `IS_DDEV_PROJECT=true`, you can use Drush to interact with a DDEV project. On the host machine, extra host-side configuration for the database and port in `settings.ddev.php` allow Drush to access the database server. This may not work for all Drush commands because the actual web server environment is not available.

On Drupal 8+, if you want to use `drush uli` on the host (or other Drush commands that require a default URI), you’ll need to set `DRUSH_OPTIONS_URI` on the host. For example, `export DRUSH_OPTIONS_URI=https://mysite.ddev.site`.

**Contributed and maintained by [@rfay](https://github.com/rfay)**
