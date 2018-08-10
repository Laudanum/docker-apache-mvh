# Apache Mass Virtual Host

Apache Mass Virtual Host for PHP and static HTML websites.

## Features

- Uses [Debian](https://hub.docker.com/_/debian/) base image
- Thin Container. Optionally uses linked [MariaDB](https://hub.docker.com/_/mariadb/) and [SMTP](https://hub.docker.com/r/panubo/postfix/) containers for those services.
- Mod PHP7.0 enabled
- Both "www" and "naked" domains are served from files found at `/srv/www/sitename`
- Mass virtual host. No additional configuration required to add additional domains. Just create the "sitename"
directory and the contents will be automatically served for the "sitename" domain.

## Environment variables

SMTP Setting:

- `SMTP_PORT`
- `SMTP_HOST`

or `--link` your smtp container. `msmtp` is used for mail delivery. So PHP `mail()` function works without configuration changes.

Proxy helper:

- `BEHIND_PROXY` - Default: False. Set to true to preload [`ProxyHelper_prepend.php`](https://github.com/panubo/php-extras/blob/master/SSLHelper_prepend.php) which will register
the remote IP and SSL status (when using compatible X- proxy headers).

Apache MPM Tuning:

- `MPM_START` - Optional: Default '5'
- `MPM_MINSPARE` - Optional: Default '5'
- `MPM_MAXSPARE` - Optional: Default '10'
- `MPM_MAXWORKERS` - Optional: Default '150'
- `MPM_MAXCONNECTIONS` - Optional: Default '0'

## Status

Jessie base is production ready.
Stretch base in testing.
