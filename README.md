# FreeBSD Admin Tools

A set of tools to aid in the DevOps style administration of FreeBSD systems.

## About

### `build-config` Lets you manage a .conf file using a modular approach.

Provide it a header (`-h`), body (`-b`), or footer (`-f`) as either a directory path or file. 
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

### `setconfig` Lets you edit a .conf file from the command line.

Provide it a file (`-f`) and the option and value to add or change.  Enclose the option and 
value in double or single quotes if nessecary.

```
setconfig \
	-f /path/to/file \
	"optionname=optionvalue"
```

#### Usage example

Change the port number a daemon will listen on.

```
setconfig -f /usr/local/etc/deamon.conf port=8080
```

### `iniconfig` Lets you edit a INI file from the command line.

Provide it a file (`-f`) and optional section name (`-s`) within the file along with the directive and 
value to add or change.   Enclose the directive and value in double or single quotes if nessecary.

If the section does not exist, it will be added.

```
iniconfig \
	-f /path/to/file \
	-s section_name \
	directvive=value
```

#### Usage example

Set the directive under the database section in the settings file.

```
iniconfig -f /usr/local/etc/settings.ini -s database user=internal
```
