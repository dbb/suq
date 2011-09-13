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

[options] is one of --help or --version
[command] is the string that will be executed with root permissions

If an [option] is found, the rest of the command string will be ignored.

Set the environment variable SUQ\_SIMULATE in order to prevent suq from
actually executing the command (the command will only be printed).
Example:
    % export SUQ\_SIMULATE=1; suq perl -le 'print "foo"'
    su -l -c 'perl -le '\''print "foo"'\' root
    % 

## Dependencies
- `Sting::ShellQuote` (Debian package `libstring-shellquote-perl`)
- Perl 5.10 or newer
- `su` (Debian package `login`)

## Bugs
Visit https://github.com/dbb/suq for the README or to report any issues.

