Building
========

Windows
-------

Software
~~~~~~~~

Download and install (in their default install paths):

- `Visual Studio 2019 Community <https://www.visualstudio.com/products/visual-studio-community-vs>`_
- `Inno Setup 5.5 Unicode <http://www.jrsoftware.org/isdl.php>`_
- `Inno Download Plugin <https://dl.zoitechat.net/misc/idpsetup-1.5.1.exe>`_
- `7-Zip <http://7-zip.org/>`_
- `gendef <https://dl.zoitechat.net/gtk-win32/gendef-20111031.7z>`_ (extract to *C:\\gtk-build*)
- `WinSparkle <https://dl.zoitechat.net/gtk-win32/WinSparkle-20151011.7z>`_ (extract to *C:\\gtk-build\\WinSparkle*)


Source code
~~~~~~~~~~~

Download the `ZoiteChat source code`_ and extract
it to somewhere. You will work in the extracted *zoitechat* folder from
now.

.. _ZoiteChat source code: https://github.com/zoitechat/zoitechat/zipball/master

GTK+
~~~~

Create a folder for GTK+, referred to as *YourDepsPath* from now (*C:\\gtk-build\\gtk* by default).
Specify the absolute path to *YourDepsPath* in *win32\\zoitechat.props*
with the *YourDepsPath* property. Download:

- `GTK+ bundle <https://dl.zoitechat.net/gtk>`_

Extract them to *Win32* and *x64* in *YourDepsPath*.

.. SEEALSO::

    If you would like to build GTK+ yourself, see this `repo <https://github.com/wingtk/gvsbuild>`_.

Language interfaces
~~~~~~~~~~~~~~~~~~~

You can skip this step, but then you won't be able to generate the
installer.
Download:

-  Perl_ 5.20 x86 (install to *C:\\gtk-build\\perl-5.20\\Win32*)
-  Python_ 2.7 x86 (install to *C:\\gtk-build\\python-2.7\\Win32*)
-  Python_ 3.6 x86 (install to *C:\\gtk-build\\python-3.6\\Win32*)

-  Perl_ 5.20 x64 (install to *C:\\gtk-build\\perl-5.20\\x64*)
-  Python_ 2.7 x64 (install to *C:\\gtk-build\\python-2.7\\x64*)
-  Python_ 3.6 x64 (install to *C:\\gtk-build\\python-3.6\\x64*)

.. _Perl: https://dl.zoitechat.net/misc/perl/
.. _Python: http://www.python.org/download/

You can use other paths, but then you must update the related properties
in *win32\\zoitechat.props* accordingly.

Building
~~~~~~~~

Open PowerShell as administrator and run::

    Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

- If you're on 32-bit Windows, this is *C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe*
- If you're on 64-bit Windows, this is *C:\\Windows\\SysWOW64\\WindowsPowerShell\\v1.0\\powershell.exe* (notice that this is the 32-bit PowerShell executable)

Open *win32\\zoitechat.sln*, right click on the *release/installer* (or
*release/copy* if you skipped the language interfaces) project and set
it as the startup project. Now you can compile from under the *Build*
menu to your taste.

If everything went fine, the resulting binaries will be found in
*zoitechat-build\\Win32* and/or *zoitechat-build\\x64*. It was easy, wasn't
it?

Unix
----

First of all, you have to install the build dependencies. Package names
differ across distros, so be creative and check meson's output
if you get an error.

Most package-managers can get the dependencies for you:

- dnf: dnf install meson 'dnf-command(builddep)' && dnf builddep zoitechat && dnf install python3-cffi
- apt: apt-get install -y meson gettext iso-codes libarchive-dev libayatana-appindicator3-dev libcanberra-dev libdbus-glib-1-dev libglib2.0-dev libgtk-3-dev liblua5.3-dev libpci-dev libperl-dev libssl-dev python3-dev python3-cffi desktop-file-utils

ZoiteChat has its source code hosted using `Git <http://git-scm.com/>`_, so you have to install Git as
well. When it's ready, you can start the actual compilation, which is
basically:

.. code-block:: bash

    git clone https://github.com/zoitechat/zoitechat.git
    cd zoitechat
    meson build
    ninja -C build
    sudo ninja -C build install

This will compile with defaults. See ``meson configure build`` for more info
about flags.

