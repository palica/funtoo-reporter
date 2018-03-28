# Funtoo-Report - v2.1.0-alpha ![CI build test badge](https://api.travis-ci.org/haxmeister/funtoo-reporter.svg?branch=feature/test-suite "Build test badge")

###### Anonymous reporting tool for Funtoo Linux

### Installation:
```
emerge -av Funtoo-Report
```

### Operation:
**The reporting tool is intended to run with root privileges for access to key
system files. Use the method most appropriate on your system**

**Just launching the program will show you a help menu:**

'funtoo-report'

```
Funtoo anonymous data reporting tool usage:

funtoo-report --config         Specify path to config file
funtoo-report --config-update  Interactively updates the config file
funtoo-report --list-config    Lists the current configuration file's settings
funtoo-report --show-json      Shows the JSON report
funtoo-report --send           Sends the JSON report
funtoo-report --debug          Enables additional debug output
funtoo-report --help           Display this help text
funtoo-report --version        Prints the version and exits

Output can be omitted by modifying the config file (default `/etc/funtoo-report.conf`):
```
**help shows you the same output:**

'funtoo-report --help'

**version shows you the script and module version numbers; ideally they should match:**

'funtoo-report --version'

**To see what data the report is generating use the show-json option:**

'funtoo-report --show-json'

**You may get an error that no config file is found:**

```

Warning!
Could not open the configuration file at /etc/funtoo-report.conf
To generate a new configuration file use 'funtoo-report --config-update'


```
**You can follow these warning instructions and the program will ask you which sections you want to enable in your config file**

'funtoo-report --config-update'

**You can send your report to the elastic search database using the send option which will return a link to the data if successful:**

'funtoo-report --send'

```your report can be seen at: http://elk2.liguros.net:9200/funtoo-2018.10/report/C5DOC2IB4MpucymM_TFy```

**You can get HTTP debugging output for the send command with the `--debug` or `-d` option:**

'funtoo-report --debug --send'

### Manual Configuration:

The reporting tool is completely anonymous and the individual categories that
are in the report can be turned off or on by editing the config file. The
config file is located at /etc/funtoo-report.conf by default, and will be
autogenerated by the script if one is not present. All lines of the config file
that are empty or start with # are ignored. The rest are read but may be
ignored if they do not match any expected setting. You can manually change the
settings from 'y' to 'n' to disable a particular category. Using the show-json
option, you can confirm that this portion of the report is not being output,
since the show-json option actually shows exactly what is reported to
elasticsearch.

**Here is an example of all possible values in the config file**

```perl
# To report kernel info including O.S. type, release and version
kernel-info:y

# Allows the reporter to search your /boot directory and list
# any kernels it finds
# (limited to kernel names that start with "kernel" or "vmlinuz")
boot-dir-info:y

# To report versions of key softwares on your system including
# portage, ego, python, gcc, and glibc
version-info:y

# To report the contents of /var/lib/portage/world
world-info:y

# To report profiles information
# the same as epro show-json
profile-info:y

# To report kit versions as reported by ego
# extracted from ego kit show
kit-info:y

# To report all installed packages (takes a few secs)
installed-pkgs:y

# To report hardware info as is typical from lspci
hardware-info:y
```

### Uninstall
We are sorry to see you go!

You can uninstall the tool by running:

```
emerge -C Funtoo-Report
```


