The first thing I did was add a non-root user for pkg building. Here is how:<br>
<br>
<b>pkgmk with fakeroot</b>

To build ports as an unprivileged user, install fakeroot. Now you can build packages by prepending the command line with fakeroot. Note that the command has to be invoked as a normal user to be effective.

 <pre>$ fakeroot pkgmk -d</pre>

prt-get with fakeroot

To extend unprivileged port building to prt-get installations (e.g. prt-get sysup, depinst, install, update...), you need to start by installing prt-get, fakeroot and sudo. Add a pkgmk user and make sure it can write in the package and source directories (you need to set up dedicated directories in /etc/pkgmk.conf for this to work, see the pkgutils section of our FAQ).

 $ useradd -m -s /bin/false pkgmk
 $ chown pkgmk /usr/ports/{distfiles,packages,work}

Add this to /etc/prt-get.conf:

 makecommand sudo -H -u pkgmk fakeroot pkgmk

Now all future runs of prt-get will build packages as an unprivileged user. 
