[![tests](https://github.com/rfay/ddev-drushonhost/actions/workflows/tests.yml/badge.svg)](https://github.com/rfay/ddev-drushonhost/actions/workflows/tests.yml) ![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

## What is ddev-drushonhost?

In DDEV v1.22.4+, the former facility to use the Drupal `drush` command on the host was removed.  That usage was always fragile, but some people liked and used it.

This add-on adds that facility again.

One-time in project:

`ddev get rfay/ddev-drushonhost`

When using drush on the host you need:

```
export IS_DDEV_PROJECT=true
```

From the former documentation:

**Warning:** We don’t recommend using `drush` on your host machine. It’s also mostly irrelevant for Drupal 9+, as you should be using Composer-installed, project-level `drush`.

If you have PHP and Drush installed on your host system and the environment variable `IS_DDEV_PROJECT=true`, you can use Drush to interact with a DDEV project. On the host machine, extra host-side configuration for the database and port in `settings.ddev.php` allow Drush to access the database server. This may not work for all Drush commands because the actual web server environment is not available.

On Drupal 8+, if you want to use `drush uli` on the host (or other Drush commands that require a default URI), you’ll need to set `DRUSH_OPTIONS_URI` on the host. For example, `export DRUSH_OPTIONS_URI=https://mysite.ddev.site`.

**Contributed and maintained by [@rfay](https://github.com/rfay)**
