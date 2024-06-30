Installing
==========

Installing takserver is a relatively straight forward process. The TAK team have
done a good job at making packages available that cover the vast majority of use
cases and they have done a good job at ensuring the process is streamlined
through bundled scripts.

takserver as a product is heavily dependent on TLS certificates to ensure safe
comunication between the server and clients. The existing documentataion will
deploy a safe product but the processes around using the certificates as
documented are ardious - especially when ATAK provides mechainsms to streamline
the administrative toil. I'll not these advanced use cases elsewhere. This page
is only about getting takserver deployed using my own interpreation of the
documentation.

.. note::
    For all of these examples I will be using Debian 12. For the most part the
    commands used will be identical for redhat based deployments with the
    exception of installing the packages themself that use `yum` (or `dnf` on
    more modern variants)

.. note::
    These deployment examples are intended for deployment reachable over the
    internet. More advanced deployments requiring VPN's are possible and require
    infrastructure, planning and procedure that extends beyond the scope of this
    documentation.

Obtaining
---------

A TAKserver distribution may be obtained from the official source at
https://tak.gov. Doing so requires a free account and acceptance of all 
applicable license terms.

There are multiple files available for download on https://tak.gov. Below is an
overview of these files and their intended uses.

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - Name
     - Purpose
   * - TAKSERVER-PUBLIC-GPG.KEY
     - Public GPG key used to verify packages.
   * - TAKSERVER-DOCKER-X.Y-RELEASE-Z.ZIP
     - Files used for containerised deployment
   * - TAKSERVER-DOCKER-HARDENED-X.Y-RELEASE-Z.ZIP
     - Files used for hardened containerised deployment
   * - TAKSERVER-X.Y-RELEASEZ.NOARCH.RPM
     - Singlse server deployment for redhat based systems (e.g. rocky)
   * - TAKSERVER-DATABASE-X.Y-RELEASEZ.NOARCH.RPM
     - Database portion of multi-server deployment
   * - TAKSERVER-CORE-X.Y-RELEASEZ.NOARCH.RPM
     - Takserver potion of multi-server deployment
   * - TAKSERVER-FED-HUB-X.Y-RELEASEZ.NOARCH.RPM
     - Federation hub for redhat systems
   * - TAKSERVER-FEDHUB-DOCKER-X.Y-RELEASE-Z.ZIP
     - Federation hub for docker
   * - TAKSERVER-FED-HUB_X.Y-RELEASEZ_ALL.DEB
     - Federation hub for debian systems
   * - TAKSERVER-CORE_X.Y-RELEASEZ_ALL.DEB
     - Server component of multi-server deployment on debian systems
   * - TAKSERVER-DATABASE_X.Y-RELEASEZ_ALL.DEB
     - Database component for multi server deployment on debian
   * - TAKSERVER_X.Y-RELEASEZ_ALL.DEB
     - Single server deployment for debian based systems
   * - DEB_POLICY.POL
     - Debian policy file


Verification
^^^^^^^^^^^^

Verification of the packages is important to ensure authenticity of the file and
that the file was not corrupted during the transfer.

Along with each of the files available on tak.gov there is an MD5 checksum of
the file. While the md5 is sufficient as a basic test to ensure data was not
corrupted in transit; it is inadequate to determine if the file was modified in
transit intentionally.

To test the md5 sum

.. code-block:: shell

  md5sum download.zip
  9e4ab05886b3140f97632936c24383fc  download.zip

Simply ensure the output of md5sum matches the one provided from tak.gov.

Verification of signature
"""""""""""""""""""""""""

Cryptographic verification of the package is substantially more robust than a
a simple checksum.

TODO


Server Deployment
-----------------

All-in-one Single Server Deployment (Quickstart)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This guide will deploy an all in one deployment on debian 12. 

Download the correct package. For me it is `takserver_5.1-RELEASE40_all.deb`


Creation of host and configure networking
"""""""""""""""""""""""""""""""""""""""""

After you have created your host you'll be running tak server on we will need to
make some changes before we can start using takserver. 

First we need to ensure that the host has a static IP. This ip could be internet
accessable or private. Refer to your providers documentation to set this up. 
This guide will be using an internet routable ip address.

Next we need to ensure that DNS is properly configured. To do this we need
to the nameserver configuration for your domain. I'll be using example.com in
these steps. My chosen hostname for the takserver is host.example.com. In my DNS
configuration control panel I need to create:-

* 'A' record for host.example.com with the IP address of the host I created.

All of these steps are necessary to ensure that TLS works properly. If the name
you are accessing the server on differs from the name used to sign the
certificate the TLS will fail and the connction will fail in turn.

.. note::
    Note down the DNS hostname you have created. You will need it at several
    points during the rest of this guide.


Upload and install of takserver
"""""""""""""""""""""""""""""""


Upload takserver_5.1-RELEASE40_all.deb to virtual machine

  scp takserver_5.1-RELEASE40_all.deb root@host.example.com:

.. note::
    Your computer may not have the `scp` command. If so and you are on windows
    an scp client may be downloaded from https://winscp.net/

Ensure all of the latest updates are applied

.. code-block::

  apt update
  apt upgerade -y

Although not always strictly necessary it is good practice to reboot after
installing updates.

.. code-block::

  sudo shutdown -r now

Get back on to SSH for the host and run the installer.

.. code-block::

  apt install ./takserver_5.1-RELEASE40_all.deb

You will be prompted to install lots of packages. These are all packages
requested by the TAK installer and they are all required. Say 'yes' if prompted
and allow the installer to run.

After the installer has completed you will be in the following situation:-

* postgres is now installed and running.
* postgis extension has been installed.
* the database has been configured and seeded
* a database user has been created for tak to use.
* The password for the database user has been saved to the the initial
  configuration file
* takserver is now installed
* takserver is stopped
* taksercer is unconfigured

.. warning::
  Don't try to start takserver yet - it will fail.

.. note::
  The software is now installed and is ready for configuration of TLS and users
  See the "Certificate Management" section of this document.

Multi Server Deployment
^^^^^^^^^^^^^^^^^^^^^^^

TODO

Multi Server Deployment (External Database)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Certificate management
----------------------

Configuration of certificate Metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To get takserver running you need to complete the generation of the TLS
certificates. This remainder of this guide will complete the generation of
certificates as per the documentation. Advanced certificate management can be
discussed in the certificates section.

takserver ships with the scripts and tools necessary to generate the required
certificates.

.. note::
    It's very important that the certificates are created as the tak user
    not using the tak user will cause the certificates to be created with the
    wrong ownership and permissions. This will cause takserver to fail during
    startup.

Configure the certificate generation process. Certificates contain within them
some information that is supposed to reflect the identity of the certificates
owner. In practice this information may be anything. There is a file in
`certs/cert-metadata` where this extra infotmation may be configured to your
liking. This file MUST be edited since the default references unset environment
variables.

.. code-block::

  su - tak
  cd certs
  vim cert-metadata.sh

Modify the cert-metadata.sh file to something like below. I suggest not changing
passwords for now although this may be something you want to do in a production
deployment.

.. code-block:: shell
  :linenos:

  # Common configuration for all certificates 
  #  Edit these fields to be appropriate for your organization
  #  If they are left blank, they will not be included.  Do not leave COUNTRY
  #  blank (you may set it to "XX" if you want to be obtuse).
  # 
  #  Values for each may be optionally set as environment variables.
  #  Replace variables such as ${STATE} and ${CITY} as needed.
  # 

  COUNTRY=US
  STATE=YourSTATE
  CITY=YourCITY
  ORGANIZATION=YourORG
  ORGANIZATIONAL_UNIT=YourORGUNIT

  CAPASS=${CAPASS:-atakatak}
  PASS=${PASS:-$CAPASS}

  ## subdirectory to put all the actual certs and keys in
  DIR=files

  ##### don't edit below this line #####

  if [[ -z ${STATE} || -z ${CITY} || -z ${ORGANIZATIONAL_UNIT} ]]; then
    echo "Please set the following variables before running this script: STATE, CITY, ORGANIZATIONAL_UNIT. \n
    The following environment variables can also be set to further secure and customize your certificates: ORGANIZATION, ORGANIZATIONAL_UNIT, CAPASS, and PASS."
    exit -1
  fi

  SUBJBASE="/C=${COUNTRY}/"
  if [ -n "$STATE" ]; then
   SUBJBASE+="ST=${STATE}/"
  fi
  if [ -n "$CITY" ]; then
   SUBJBASE+="L=${CITY}/"
  fi
  if [ -n "$ORGANIZATION" ]; then
   SUBJBASE+="O=${ORGANIZATION}/"
  fi
  if [ -n "$ORGANIZATIONAL_UNIT" ]; then
   SUBJBASE+="OU=${ORGANIZATIONAL_UNIT}/"
  fi


Generate Certificate authority
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

With the certificate generation process configured it is now time to generate
the root certificate authority. This certificate will be used to establish trust
between servers and clients through signing every other certificate. takserver
contains a dedicated script to creating this certificate authority.

.. code-block::
  
  $ ./makeRootCa.sh
  Please give a name for your CA (no spaces).  It should be unique.  If you
  don't enter anything, or try something under 5 characters, I will make one for
  you.

You will be prompted to enter a name for the CA. This should be unique but and
easily identifyable.

The certificate authority is now bootstrapped. At this point you may choose to
create a multi tiered authority throug the creation of an intermediate
certificate. I won't be documenting this technique here due because I want to
write an entire section on it.



Generating the Server Certificate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Now generate the server certificate signed by the CA. Remember the hostname we
provided the server earlier. Use that Hostname HERE.

.. code-block:: shell
  
  ./makeCert.sh server host.example.com

.. note::
  THe hostname used in the command MUST mach the DNS hostname that you use to
  access the server.

Certain features of the user interface, especially when opening ports require
takserver.jks to exist. Therefore we have to make the file that we just created
(`certs/files/host.example.com.jks`) as `certs/files/takserver.jks` so that
these interface components don't break. To do this we create a symbolic link.

.. code-block:: shell

  cd certs/files
  ln -s host.example.com.jks takserver.jks

Start the TAK server
^^^^^^^^^^^^^^^^^^^^

Now we have enough configuration to start the server. Go ahead and run.

.. code-block:: shell
  
  systemctl enable --now takserver

  # this is the equivilent of:
  # systemctl enable takserver 
  # systemctl start takserver

If you are running takserver on a device with limited resources such as a
raspberry pi it is possible to run the server with reduced functionality.

.. code-block:: shell
  
  systemctl enable --now takserver-noplugins

  # this is the equivilent of:
  # systemctl enable takserver-noplugins 
  # systemctl start takserver-noplugins

.. note::
    takserver takes a bit of time to start. try not to be impatient.

I like to use ss (modern netstat) to monitor for takserver readiness. When the
command belos returns 3 lines. the important parts of tak are functioning and
you should be safe to move on.

.. code-block:: shell

  ss -antpl | grep -E (8443|8446|8089)


Generating Admin Certificate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Next we need to generate the first user certificate for the administrative user.

.. code-block:: shell

  ./makeCert.sh client administrator

This generates the certificate but no permissions have been allocated. Since the
default permission model uses mTLS to authenticate the users; a user with a valid
certificate will be able to authenticate as a regular user. We need to assign
the permission against the fingerprint of the certificate that to identify the
certificate an administrative user. To do this we use utils/UserManager.jar. 

.. note::
  The takserver must be started and fully operational for the UserManager.jar
  command to be successful.

To make the administrator an administrative user user the UserManager.jar

.. code-block:: shell

  cd /opt/tak
  java -jar utils/UserManager.jar certmod -A certs/files/administrator.pem

Keep in mind the last arguement to this command is the **.pem** file. This is
not the file that you will distribute to the users but the pem the p12 the jks
all contain the same certificate, the pem does not contain the private key while
other files do.

Distributing the admin certificate and connecting to the admin interface
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can find the admin certificate in `certs/files/administrator.p12`

Obtaining access to the administrative interface is straight forward. Transfer
this file to the clients device. 

Open the users web browser. Import Certificates and import the administrator.p12
file in to the users certificate store. Unless you changed it the import
password is 'atakatak'. This file by default contains the CA certificate used to
sign the client certificate and the server certificate. For TLS to work properly
this certificate needs to be marked as trusted. In the list of certificate
authorities locate the CA certificate and edit it's trust. Ensure that it may
be used to identify web sites.

Now time to access the admin interface. In your web browser navigate to the
administrative interface at https://server.example.com:8443 (the name you set
earlier). You should be prompted to select a certificate. Select the
administrator certificate and optionally "remember this decision". Press OK.

If everything worked properly you should be shown the takserver dashboard.


Generating User Certificates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

User certificates i.e. unprivileged certificates. Is exactly the same as
generating the Administrative certificate but the `UserManager.jar certmod`
command is not run.

.. warning::
  DO NOT provide regular users with administrative certificates.

When distributing the certificates to users for importing in to ATAK/WINTAK etc
you will also need to provde `truststore-root.p12`

