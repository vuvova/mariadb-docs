# buildbot-setup-buildbot-setup-for-windows

## Buildbot Setup for Windows

This is the recipe for setting up a MariaDB Buildbot slave on Windows:

1. Prepare the [development environment](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/getting-installing-and-upgrading-mariadb/compiling-mariadb-from-source/Building_MariaDB_on_Windows)
2. Install [Python](https://www.python.org/download/), 32 bit. Twisted does not work on 64 bit and builtbot hasn't been tested properly with Python version 3.\
   Note: As of June 2016, there is no fresh Twistd for 32-bit Python, so a 64-bit version has to be installed. Installed 2.7.11 64-bit, it seems to work.
3. Install [pywin32](https://sourceforge.net/projects/pywin32/files). Make sure the version matches your Python version perfectly, and get the .exe file, not the zip file.\
   Note: As of June 2016, used `pywin32-220.win-amd64-py2.7.exe`, it seems to work.
4. Install [Twisted](https://twistedmatrix.com/trac/wiki/Downloads)\
   Note: As of June 2016, used `Twisted 16.2.0 for Python 2.7 64 bits`
5. Install [buildbot](https://buildbot.net): Get the zip file and unpack it. In an administrator shell, cd to the buildbot dir and run "python setup.py install". After that, the unpacked buildbot directory is no longer needed.\
   Note: As of June 2016, used `buildbot 0.8.12`.

When this has been done, you run these commands:

```
cd <somewhere>
mkdir buildbot
cd buildbot
bzr init-repo .
C:\buildbot\buildbot-slave-0.8.3\build\scripts-2.7\buildslave.bat create-slave --usepty=0 <slavedir> hasky.askmonty.org:9989 <slavename> <passwd>
```

Adjust paths in the last command according to the location of your unpacked buildbot.

You get and from one of the MariaDB Corporation or MariaDB Foundation people handling the buildbot system. can be whatever you want - is a good choice.

Please edit the files \info\admin and \info\host with your information. The host information should include your Windows version, 32 or 64 bit, and your Visual Studio version.

You can test the buildbot slave with this command:

```
C:\buildbot\buildbot-slave-0.8.3\build\scripts-2.7\buildslave.bat start <somewhere>\buildbot\<slavedir>
```

When buildbot starts, you should confgure it as a service instead of manually. See the instructions [here](https://buildbot.net/trac/wiki/RunningBuildbotOnWindows). It's under the section "Windows Buildbot service setup". This document also has the generic Windows Buildbot installation documentation.

### Why buildbot should run as service

When buildbot is running in user session, and application that is started by buildbot crashes, you'll get a crash popup. There are popups that are generated by post-mortem debugging and there are popups that are generated by Windows Error reporting. It is hard (or impossible for those who did not try this before) to get rid of all popups. Thus, do run buildbot as service. There are no popups in services.

### Common Windows Buildbot Failures

#### Test hangs after trying to call cdb to print a backtrace.

MTR attempts to call `cdb` via the Perl backticks operator, when mysqld.exe crashes. On the first run, cdb is downloading public Windows symbols from msdl.microsoft.com/download/symbols. The symbols are cached in C:\cdb\_symbols, and following runs will be faster, however crashdump analysis on very first crash will typically take some time.

If you find this bothering, start the test with `--mysqld=--gdb` which will cause no crashdump files to be created and thus will prevent `cdb` from being called.

#### Buildbot exception `The process cannot access the file because it is being used by another process`

This is due to the fact that buildbot does not clean up any processes left over from a previous run, and those processes may hold locks on files that are needed for a new build to start. Current workaround is to use windows job objects that allow to terminate entire process trees. We use special "process launcher" utility called "`dojob` . This will also require changing buildbot configuration for the builder.

Download [dojob.cpp](https://bazaar.launchpad.net/~maria-captains/mariadb-tools/trunk/view/head:/buildbot/dojob.cpp), and compile it with

```
cl dojob.cpp
```

Then, put dojob.exe into a directory in the PATH [environment variable](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/mariadb-environment-variables).\
Then, change buildbot configuration to use "dojob" for every command, as a replacement for "cmd /c", e.g

```
factory.addStep(Compile(
        name = "cmake",
        command=["dojob", WithProperties("cd c:\\buildbot\\%(buildername)s\\build && cmake .")]
));
```

#### Buildbot exception `ShellCommand.failed: command failed: SIGKILL failed to kill process`

(Seen very seldom?). This usually happens after retrying multiple failing tests multiple times. It appears that MTR's `--retries=` option is not safe to use on Windows. The solution is to run the test with no `--retries`.

#### Buildbot exception `Connection to the other side was lost in a non-clean fashion.`

This is a sympthom of intermittent network issues, which cause Buildbot to abort the current build altogether. The following workarounds are possible:

* In your `buildbot.tac` file, specify a higher `keepalive` value, such as 60000.\
  Note: For the current versions (as of June 2016), the opposite solution worked: keepalive = 60. KeepAliveTime in the Windows registry has been set to 60000 as suggested below, but there is no proof it made any difference.
* If you are running the Windows host inside VMWare, substitute the `e1000` network adapter with `vmxnet3`
* If your build host is behind a firewall, makes sure that the firewall does not time out any idle connections quickly. Configure at least a 24-hour timeout.
* If your build host is behind a firewall, consider disabling the built-in Windows Firewall in order to avoid one potential point of failure.
* Modify the Windows `KeepAliveTime` registry setting to a lower value, such as 60000 (equal to 60 seconds). For more information, see [TechNet](https://technet.microsoft.com/en-us/library/cc957549.aspx)
* Make sure the buildbot master does not experience prolonged bouts of 100% CPU activity, as this may prevent keepalives from working. If the buildbot master `twisted.log` says that data is frequently being loaded from on-disk pickles, increase the `buildCacheSize` in the master configuration file to be more than the number of builds per builder that the log file reports are being loaded.

## Alternative Windows Buildbot setup (experimental)

In case the default Windows buildbot setup is not sufficiently reliable due to "connection lost in a non-clean fashion" errors, the following setup can be used\
instead. It runs the buildbot deamon on a linux host while doing the builds on Windows, thus working around Twisted issues on Windows.

**Note that the procedure below&#x20;**_**significantly**_**&#x20;degrades the overall security of your Windows host. It is strongly recommended that a properly-firewalled, standalone virtual machine is used.**

* Set the Windows server to auto-login with the user the builds will run as. This will prevent any issues relating to running things as a service and the privilege considerations associated with services;
* Install FreeSSHd on Windows. The OpenSSHd/Cygwin combo is not likely to work.
  * Do not run FreeSSHd it as a service, but rather as a startup console application for the user you are running the builds under. This allows FreeSSHd UI to properly operate;
  * Generate a private/public key pair using PuTTYGen and place the public part in a properly named file in the key directory specified in the FreeSSHd GUI
  * Using the FreeSSHd GUI, create a new user and set it to use key authentication;
  * Set the SFTP home path to the directory where builds will take place.
* Disable UAC (User Access Control) (or set to lowest level) by using the Users Control Panel. Add your buildbot user to the Administrators group.
* Export the private key from PuTTYGen and copy it to a Linux host.
* Install buildbot on the Linux host
* The buildbot configuration file will then look something like:

```
f_win2008r2_i386_release.addStep(ShellCommand(
        command=["ssh", "-i", "/home/buildbot/keys/id_rsa", "buildbot@win2008r2-build", "cmd", "/C", "whoami"]
));
```

The following buildbot considerations apply under this setup:

* buildbot will not perform a proper cleanup of the build directory on the Windows host before each build (it will only clean up things on the linux side). So, a directory cleanup via rmdir must be placed as an explicit first step in the build sequence;
* Bzr() can not be used to check out BZR trees, as it expects that the bzr checkout command will run locally. Instead, an explicit call to bzr checkout via a SSH command must be used;

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
