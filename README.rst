Directories needed
==================
Key directory (key-dir)
-----------------------
A directory containing all the public keys for the keys added to keyholder.
The files must be named ``[keyname].pub``

Config directory (auth-dir)
---------------------------
A directory containing one or more YAML files (extension must be yml or yaml) with permission information. A YAML file must have one or more sets of a unix group name  followed by a list of keynames (the same keyname as used in the filename previously)

::

    [groupname]
      - [keyname]


Keyholder
=========

keyholder provides a means of allowing a group of trusted users to use a
shared SSH identity without exposing the identity's private key.

The agent binds the socket at this address by default

::

    /run/keyholder/agent.sock (0666)

Before the shared SSH agent can be used, it must be armed by a user with
access to the private key. This can be done by running:

::

    $ /usr/sbin/keyholder arm

Users in the trusted group can use the shared agent by running:

::

    $ SSH_AUTH_SOCK=/run/keyholder/agent.sock ssh remote-host ...

License
-------

`Apache 2.0 <https://www.apache.org/licenses/LICENSE-2.0>`__
