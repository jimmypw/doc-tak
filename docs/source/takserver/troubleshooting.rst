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
`-noplugins` variant does not start the plugin manager service, nor the
retention service. Most users can get by using the `noplugins` unit.

These units in turn call init scripts in `/etc/init.d`

takserver.unit calls:

* /etc/init.d/takserver-config (start|stop)
* /etc/init.d/takserver-messaging (start|stop)
* /etc/init.d/takserver-api (start|stop)
* /etc/init.d/takserver-plugins (start|stop)
* /etc/init.d/takserver-retention (start|stop)

takserver-noplugins calls:

* /etc/init.d/takserver-config (start|stop)
* /etc/init.d/takserver-messaging (start|stop)
* /etc/init.d/takserver-api (start|stop)

These secondary init scripts when starting call scripts within /opt/tak:

* /etc/init.d/takserver-config -> /opt/tak/takserver-config.sh
* /etc/init.d/takserver-messaging -> /opt/tak/takserver-messaging.sh
* /etc/init.d/takserver-api -> /opt/tak/takserver-api.sh
* /etc/init.d/takserver-plugins -> /opt/tak/takserver-plugins.sh
* /etc/init.d/takserver-retention -> /opt/tak/takserver-retention.sh

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

It is also possible to start individual microservices

.. code-block:: shell

    /etc/init.d/takserver-config start
    /etc/init.d/takserver-messaging start
    /etc/init.d/takserver-api start
    /etc/init.d/takserver-plugins start
    /etc/init.d/takserver-retention start

Stopping
^^^^^^^^

To stop takserver (if started)

.. code-block:: shell

    # use one of below
    systemctl stop takserver
    # or
    systemctl stop takserver-noplugins

It is also possible to stop individual microservices

.. code-block:: shell

    /etc/init.d/takserver-config stop
    /etc/init.d/takserver-messaging stop
    /etc/init.d/takserver-api stop
    /etc/init.d/takserver-plugins stop
    /etc/init.d/takserver-retention stop

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

Logging
-------

