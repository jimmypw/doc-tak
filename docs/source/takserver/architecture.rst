Architecture
============

Takserver is a collection of microservice components that work together. Each
of these microservices have a specific purpose. 

* Config
* API
* Messaging
* Retention
* Plugins

.. note::
    The ports provided below are in reference to the default ports that are 
    opened by the microservice in use as per the default configuration. These
    ports and purposes may change after configuration. I have not documented 
    outgoing connections.

Config
------

.. note::
    Although the core config does open ports they listen on 127.0.0.1 and are
    for internal use only. Since these numbers or purposes may change I won't
    document them here.


The primary microservice for providing consistent configuration across all of
the microservices. Thi microservice must be the first microservice started as
the messaging and api microservice depend on it functioning correctly.

API
---

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - Port
     - Purpose
   * - 8443
     - Admin Interface / WebTak / Uploads / Downloads
   * - 8444
     - Federation related. Exact purpose unknown.
   * - 8446
     - Certificate enrollment / WebTak


* Handles all HTTP traffic
* Provides admin API
* Provides user api (uploads / downloads etc...)

Messaging
---------

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - Port
     - Purpose
   * - 8089
     - Client connection port


The primary endpoint for all data clients weather atak users, data streams etc..

Retention
---------

.. note::
  Although the retention process is running, the maintenance jobs it performs
  are disabled by default.

The retention service is a background process that monitors and prunes old data
held by the tak server. This may be configured by the user interface under 
Administrative -> Data Retention. The configuration is stored on disk under:
`conf/retention`

Plugins
-------

The takserver plugin manager service. For thoe most part this service is
redundant since there aren't many if any takserver plugins available publicly.

.. note::
  Did you know you can disable the takserver plugin manager by using the 
  `takserver-noplugins` systemd unit.
