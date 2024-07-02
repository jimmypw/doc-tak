Troubleshooting
===============

Takserver can be straight forward to set up however when takserver goes wrong it
can be a challenge to know where to find the right information to fix it. In the
sections below I will share some of the comon techniques I use to identify and
solve these problems.

Most of these commands are common system administration techniques. There are
many more

Systemd
-------

.. note::
    If you are using a containerised deployment of takserver you are likely not
    using systemd so skip this section.

.. note::
    takserver doesn't use systemd units. instead it uses init scripts that are
    wrapped with a systemd unit. As a result the systemd units don't provide
    much information about the process other than the script it's running to
    start / stop takserver.

Although takserver ships with init scripts rather than with true systemd units,
systemd is the defacto init process for all supported operating systems and you
must use systemd to manage the takserver.

Tak ships with two unit files

* takserver
* takserver-noplugins

These two units are essentially the same. The difference is that the
`-noplugins` variant does not start the plugin manager service. Most users can
get by using the `noplugins` unit.

Status
^^^^^^

To obtain the status of takserver - if it's running or not or if it has failed.

.. code-block:: shell

    # use one of below
    systemctl status takserver
    # or
    systemctl status takserver-noplugins

Starting
^^^^^^^^

To start takserver (if stopped)

.. code-block:: shell

    # use one of below
    systemctl start takserver
    # or
    systemctl start takserver-noplugins

Stopping
^^^^^^^^

To stop takserver (if started)

.. code-block:: shell

    # use one of below
    systemctl stop takserver
    # or
    systemctl stop takserver-noplugins


Enabling at boot
^^^^^^^^^^^^^^^^

If your takserver does not come online when the server is started

.. code-block:: shell

    # use one of below
    systemctl enable takserver
    # or
    systemctl enable takserver-noplugins

Disabling at boot
^^^^^^^^^^^^^^^^^

If you do not want takserver to come online when the server is started

.. code-block:: shell

    # use one of below
    systemctl enable takserver
    # or
    systemctl enable takserver-noplugins