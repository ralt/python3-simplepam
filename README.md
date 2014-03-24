python3-simplepam
=================

An interface to the Pluggable Authentication Modules (PAM) library on linux,
written in pure python (using ctypes)

Overview
--------

This module provides an ``authenticate`` function that allows the caller to
authenticate a given username / password against the PAM system on Linux.

Usage
-----

Run ``python3 setup.py install`` as root to install the module, then import the
``authenticate`` function, and use it as follows:

```python
    from simplepam import authenticate
    authenticate(username, password, service)
```

The ``service`` argument specifies the PAM service to authenticate against.
Defaults to ``login``.

The function returns ``True`` if the authentication succeeds and returns
``False`` if authentication fails (or if PAM returns an error (FIXME)).

License
-------

The [original python-pam module](http://atlee.ca/software/pam/) was written by
Chris AtLee, see the original copyright notice:

    Copyright (C) 2007-2009 Chris AtLee <chris@atlee.ca>.
    Licensed under the MIT license. 

Modifications 2013-2014 by Leon Weber <leon@leonweber.de>:
* Ported to Python3
* Add call to ``pam_end()``
* Use ``ctypes.byref()`` instead of ``ctypes.pointer()`` to pass arguments by reference
* Properly handle encoding of password, username and service (Patch by Sebastian
  Riese)
* Re-add Python2 support (Patch by Victor Stinner of eNovance)

This module is licensed under the [MIT license](http://www.opensource.org/licenses/mit-license.php).
