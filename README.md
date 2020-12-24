# FreeBSD Admin Tools

A set of tools to aid in the administration of FreeBSD systems.

## About

### `build-config` Lets you manage a .conf file using a modular approach.

Provide it a header (`-h`), body (`b`), or footer (`f`) as either a directory path or file. 
It will merge all items togehter to create a single file that will be printed on the standard output
or to a file provided by the `-o` option.

The `-e` option can be provided (without the dot) to override the default file extension (`conf`) that will be used to search for
files when a directory is provided as input.

```
build-config \
	-h /path/to/file/or/directory \
	-b /path/to/file/or/directory \
	-f /path/to/file/or/directory \
	-o /path/to/file \
	-e file_ext
```

#### Usage example

Manage your FreeBSD jails as individual config files in a directory instead of having to edit a
monolithic configuration file.

```
build-config -h /usr/local/etc/jail.d/header.inc -b /usr/local/etc/jail.d -o /etc/jail.conf
```
