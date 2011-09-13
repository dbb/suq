# suq 

<http://github.com/dbb/suq>

## Description
`suq` is a Perl script that uses the command line arguments passed to it to
form a properly quoted command string that is then passed to `su` to be
executed as root. It is desgined as an alternative to the common usage of
`sudo` to execute a single command with root privileges. This is useful for
systems on which `sudo` is not installed or is unnecessary.


## Usage
`suq [options] [command]`

`[options]` is one of `--help` or `--version`
`[command]` is the string that will be executed with root permissions

If an `[option]` is found, the rest of the command string will be ignored.

## Environment variables
`suq`'s behavior is controlled by the following environment variables:

* `SUQ_NOLOGIN=1`           do *not* pass '-l' to su
* `SUQ_PRESERVE=1`          pass "-m" to su
* `SUQ_SHELL='shell'`       pass "-s shell" to su
* `SUQ_SIMULATE=1`          print the command; don't run it
* `SUQ_USER='name'`         run command as "name" instead of root

Set the environment variable `SUQ_SIMULATE` in order to prevent suq from
actually executing the command (the command will only be printed).
Example:
```
    % export SUQ_SIMULATE=1; suq perl -le 'print "foo"'
    su -l -c 'perl -le '\''print "foo"'\' root
    % 
```
The default value of all aforementioned ENV variables is undefined. Setting a
value to '' or 0 will cause it to be ignored (i.e. return it to the default
value) except for `SUQ_USER`, which is treated as a string. To reset it:
`export SUQ_USER='root'`


## Dependencies
- `Sting::ShellQuote` (Debian package `libstring-shellquote-perl`)
- Perl 5.10 or newer
- `su` (Debian package `login`)

## Bugs
Visit https://github.com/dbb/suq for the README or to report any issues.

