Introduction
============

TAK server is a java application that acts as a central server for multiple TAK
clients to connect to. Connected clients may then exchage data. The TAK server
has many features to facilitate and manage this.

* User Management
* User Federation
* Certificate Enrollment
* Certificate Management
* Data Management
* Data Ingestion and Routing
* WebTak
* Server Federation
* Plugin System


Supported Operating Systems
---------------------------

TAKserver is officially support on Debian and Redhat derrived operating Systems
and packages are provided for each system. Packages are also provided for docker 
meaning TAKServer may be run on any reasonably modern operating system,
including Windows and MacOS.


System Requirements
-------------------

TAK server has very few system requirements and may be run on as little as a
Raspberry PI 4 (8GB). The amount of reources required will depend heavily on:-

* Use Case
* Number of Users
* Chosen deployment architecture

For a ball park figure. A small deployment supporting up to 500 users on a
single server setup and no data feeds would require around the following
specification.

* 64 bit OS: Debian 12, Ubuntu 22.04, Raspberry PI OS (Based on debian 12), Rocky 8, Redhat 8 OR Docker
* 4 Core CPU
* 8GB ram
* 100GB SSD
* 100mbps Connection

Although a raspberry pi may be able to meet these specifications and will run 
just fine for very small deployments. The platform is very under powered and 500
concurrent users may be stretching the platforms limited power too far.

.. note::
    Sizing TAKserver exactly is difficult. In general more resources lead to a
    better experiance.


Dependencies
------------

TAKserver depends on:-

* OpenJDK 17 JDK
* PostgreSQL 15
  * With Postgis extension
* Openssl - Soft dependancy for certificate management.

And docker if that is your chosen deployment mechanism.


Source code
-----------

.. note::
  The TAKserver source code lags behind the release available on tak.gov. For
  example; the latest release on tak.gov is currently 5.1-RELEASE-40 and the
  latest release available on github is 5.1-RELEASE-8

TAKserver is open source. The available source code lags slightly behind the
current release. The code is available from the official github repository
at https://github.com/TAK-Product-Center/Server
