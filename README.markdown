This fork exists as a workaround to a specific problem I was having. I had a drive 
fail with 512 byte sector size, and the replacement that I purchased had 4K sectors.
This would lead to an error in the zpool replace command:

    sudo zpool replace tank oldDisk newDisk -f
    cannot replace oldDisk with newDisk: devices have different sector alignment

I patched the code to use the logical sector size instead of the physical sector size,
which then allowed the replacement to succeed.

----

Native ZFS for Linux! ZFS is an advanced file system and volume manager
which was originally developed for Solaris. It has been successfully 
ported to FreeBSD and now there is a functional Linux ZFS kernel port
too. The port currently includes a fully functional and stable SPA, DMU,
and ZVOL with a ZFS Posix Layer (ZPL) on the way!

    $ ./configure
    $ make pkg

To copy the kernel code inside your kernel source tree for builtin
compilation:

    $ ./configure --enable-linux-builtin --with-linux=/usr/src/linux-...
    $ ./copy-builtin /usr/src/linux-...

Full documentation for building, configuring, and using ZFS can be
found at: <http://zfsonlinux.org>
