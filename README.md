# Role `php-fpm`

Role to install and configure *php-fpm* in given versions.


## Description

This role will add extra *deb.sury.org* repository and install php-fpm with
defined *extensions* in all given *php versions*.

A default php-fpm *pool* (for `www-data` user) is created for all given
*versions*.


## Variables

| Variable                  | Required  | Default                             | Description |
| ------------------------- | --------- | ----------------------------------- | ----------- |
| php_installed_versions    | no        | [ 7.3 ]                             | List of desired PHP versions; See `deb.sury.org` repository for currently supported versions |
| php_default_version       | no        | `php_installed_versions[0]`         | Default php version configured on the system |
| php_extensions            | no        |                                     | List of PHP extensions to install |
|                           |           |                                     |  |
| php_extra_parameters      | no        |                                     | List of extra php admin values to configure in default php pools |


## Examples

Install php-fpm 7.4 with some extensions:

```yaml
php_version:
  - '7.2'

php_extensions:
  - curl
  - gd
  - json
  - mbstring
  - mysql
  - zip
```

Configure some `upload_max_size` in default pools:

```yaml
php_extra_parameters:
  upload_max_filesize: '48M'
  post_max_size: '64M'
  memory_limit: '80M'
```
