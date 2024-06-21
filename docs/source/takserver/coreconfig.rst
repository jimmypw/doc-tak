CoreConfig.xml
==============

<network>
---------

<filter>
^^^^^^^^

<input>
^^^^^^^

<filtergroup>
"""""""""""""

TODO


<filter>
""""""""

TODO

@_name
""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - string
   * - **Default**
     - none
   * - **Description**
     - Name of the input


@port
"""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - integer
   * - **Default**
     - none
   * - **Description**
     - The port number assocaited with this input.

@auth
"""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - x509
   * - **Description**
     - The authentication associated with this input options are:

       * x509
       * ldap
       * anonymous
       * file

@authrequired
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false
   * - **Description**
     - TODO


@protocol
"""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - string
   * - **Default**
     - none
   * - **Description**
     - Protocol in use by input
       
       * tcp
       * udp
       * tls

@group
""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none
   * - **Description**
     - Group name associated with the input


@iface
""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none
   * - **Description**
     - Host insterface name to listen on

@archive
""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true
   * - **Description**
     - TODO


@anongroup
""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - none
   * - **Description**
     - TODO

@archiveOnly
""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false
   * - **Description**
     - TODO

@coreVersion
""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - 2
   * - **Description**
     - TODO


@syncCacheRetentionSeconds
""""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - 3600
   * - **Description**
     - TODO

@maxMessageReadSizeBytes
""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - 2048
   * - **Description**
     - TODO


@coreVersion2TlsVersions
""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - TLSv1.2,TLSv1.3
   * - **Description**
     - TODO

@federated
""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true
   * - **Description**
     - TODO


@binaryPayloadWebsocketOnly
"""""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false
   * - **Description**
     - TODO

@quicConnectionTimeoutSeconds
"""""""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - long
   * - **Default**
     - 90
   * - **Description**
     - TODO

<connector>
^^^^^^^^^^^

@port
"""""

What port does the connector listen on

@useFederationTruststore
""""""""""""""""""""""""

use fenderateion trust store 

@_name
""""""

@clientAuth
"""""""""""

clientAuth

@keystoreFile
""""""""""""""

keystoreFile

@keystorePass
"""""""""""""

keystorePass

@truststoreFile
"""""""""""""""

truststoreFile#

@truststorePass
"""""""""""""""

truststorePass


<auth>
------

<submission>
------------


<subscription>
--------------


<repository>
------------


<repeater>
----------


<filter>
--------


<buffer>
--------


<dissemination>
---------------


<certificateSigning>
--------------------


<logging>
---------


<security>
----------


<ferry>
-------


<async>
-------


<federation>
------------


<geocache>
----------


<citrap>
--------


<xmpp>
------


<plugins>
---------


<cluster>
---------


<docs>
------


<email>
-------


<locate>
--------


<vbm>
-----


<profile>
---------
