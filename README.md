# Apache Mass Virtual Host

Apache Mass Virtual Host for Perl and static HTML websites:

More information:

- [Jessie Base](jessie) (legacy)
- [Stretch Base](stretch) (recommended)
- [Buster Base](buster) (in testing)

## Build

```
$ make build
```

## Run

```
$ make run
```

## Connect
```
$ make shell
```

## Testing locally

1. Create directories
    `$ mkdir -p srv/www srv/remote srv/www/perl.example.com`
1. Add a line to the hosts `/etc/hosts` file
1. Create some files `srv/www/perl.example.com/index.html`
1. Create Mountfile `srv/www/perl.example.com/Mountfile`
1. Run docker with volumes
   ```
   $ docker-compose up
   ```
1. Connect
   ```
   $ docker exec -ti stretch_apache-perl_1 /bin/bash
   ```
1. Browse
    http://perl.example.com:81/

After making changes to entry.sh `make clean && make build`
