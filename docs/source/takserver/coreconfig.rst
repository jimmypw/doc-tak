CoreConfig.xml
==============

The CoreConfig.xml file is the primary configuration file. It is written in xml
and it is read from various TAKserver processes to retrieve the configuration
that is relevant to it.

The options in this file have been interpreted from CoreConfig.xsd which is the 
XSD schema that validates the corresponding XML file. The functionality
associated with the configuration directive is either known or is still yet to
be deciphered from reading the code.

Many of the features that TAK Server provides may be configurated from the
Administration interface. There are still many features that are not exposed
through the admin interface and must be configured manually. In addition having
a complete reference for the CoreConfig.xml can greatly assist with automated
deployment.

<network>
---------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true

The network element configures network input/output and configures
security settings for those connections such as authentication,
authorisation and encryption.

@multicastTTL
^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 1

TTL of multicast packets

@serverId
^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

A unique string representing the server ID. 

TODO: How is this used exactly? I expect it is used during federation.


@enterpriseSyncSizeLimitMB
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 400

Sets the size limit for file uploads in MB.

@enterpriseSyncSizeUploadTimeoutMillis
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 600000

Set the timeout for file uploads in milliseconds (sync/upload endpoint).

@enterpriseSyncSizeDownloadTimeoutMillis
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 600000

Set the timeout for file downloads in milliseconds (sync/upload endpoint).

@missionPackageAutoExtractSizeLimitMB
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 10

TODO

@httpSessionTimeoutMinutes
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 130

TODO

@extWebContentDir
^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - webcontent

TODO

@takServerHost
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO

@useLinuxEpoll
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO

@allowAllOrigins
^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO

@enableHSTS
^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO

@esyncEnableCache
^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 0

TODO

@esyncEnableCotFilter
^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO

@esyncCotFilter
^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO

@version
^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

Specifies the version of software that the server is running.


@webCiphers
^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

TODO

@tomcatPoolIdleToMax
^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

Set tomcat idle threads to configured max.

@tomcatMaxPool
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - -1

Explicity set the size for Tomcat service thread pool. multiplier for
autodetected ignite thread pool size. The optimal value varies based on system
capabilities (CPU core count).


@tomcatPoolMultiplier
^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 32

Set the multiplier for autodetected ignite thread pool size. The optimal value
varies based on system capabilities (CPU core count).


@cloudwatchNamespace
^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - takserver

TODO

@cloudwatchMetricsBatchSize
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - int
   * - **Default**
     - 20

TODO

@cloudwatchEnable
^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO

@cloudwatchName
^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

TODO

@missionCopTool
^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - vbm

TODO


@pingTimeoutSeconds
^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - none

TODO

@pingTimeoutCheckIntervalSeconds
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - 60

TODO

@alwaysArchiveMissionCot
^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO

@MissionCreateGroupsRegex
^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO

@MissionDeleteRequiresOwner
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO




<filter>
^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO

<input>
^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

This element may be specified as many times as necessary. Each input
represents a COT client. This could be for example I/ATAK or another COT
generating data source.
  
<filtergroup>
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO.


<filter>
""""""""


.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

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

Name of the input


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

The port number assocaited with this input.

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

The authentication associated with this input options are:

* x509
* ldap
* anonymous
* file

.. note::
  Certain options require other options to be set e.g. LDAP requires an LDAP
  server to be configured.

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

TODO


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

Protocol in use by input
       
* tcp - standard tcp. 1 message per connection.
* stcp - streaming tcp. multiple messages per connection.
* udp - one message per packet
* tls - secure streaming tcp (tls) CoT or Protobuf
* grpc - secure streaming with GRPC
* cottls - secure streaming TCP (cottls) CoT only

.. note::
  Make sure you correctly specify your protocol else the input will malfunction.

  E.g. Sending a streamed tcp message in to a standard tcp port will result in
  only the last message being propagated to clients.


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

Group name associated with the input as if the input was in the 'in' group.


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

An optional valid network interface name (e.g., en0).

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

TODO


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

TODO

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

TODO

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

COT message version:-

* 1 - levacy
* 2 - modern (high performance)


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

TODO

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

TODO


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

TODO

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

TODO


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

TODO

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

TODO


<dataFeed>
^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO - it looks like <dataFeed> extends <input> and also has some extra elements
i need to look a bit closer at this.


<connector>
^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

Represents HTTP connectors that are routed to TAKserver components. Examples of
these components could be Administration interface, data package repository,
certificate enrollment.

@_name
""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

The name of the connector

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

What port does the connector listen on

@useFederationTruststore
""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

use fenderateion trust store to authenticate incoming MTLS connections.


@clientAuth
"""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - true

TODO - this attribute is interesting since the type is a string but the Default
value is a boolean. I wonder what other options exist.

@keystore
""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO

@keystoreFile
""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

Path to a keystore that contains the certificates that will be presented to
connecting clients

@keystorePass
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

The keystore password associated with the corresponding @keystoreFile


@truststore
"""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO

@truststoreFile
"""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

Path to a truststore that contains the certificates that will be used to
validate certificates presented by connecting clients.

@truststorePass
"""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

The password associated with the corresponding @truststoreFile

@enableAdminUI
""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

Enables the admin user interface on this port.

@enableWebtak
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

Enables webtak interface on this port.

@enableNonAdminUI
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO - i'm not sure what's intended by "non-admin ui" possibly the monitoring
interface. Or it could mean the data package interface.

@allowOrigins
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

TODO - Likely CORS settings

@allowMethods
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - POST, PUT, GET, HEAD, OPTIONS, DELETE

TODO - Likely CORS settings


@allowHeaders
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - Accept, Access-Control-Allow-Headers, Authorization, Content-Type, Cookie, Origin, missionauthorization, X-Requested-With

TODO - Likely CORS settings

@allowCredentials
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO - Likely CORS settings

<auth>
------

<ldap>
^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

Configures a connection to an LDAP server such as OpenLDAP or Active Directory
used for authentication

<filtergroup>
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string

Must appear first in the <ldap> element if used. May be used multiple times.

TODO: not sure on the functionality


@url
""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - string
   * - **Default**
     - none

TODO

URL of ldap server to connect to

Example: ldaps://


@userstring
"""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - string
   * - **Default**
     - none

UNKNOWN/TODO


@updateinterval
"""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - integer
   * - **Default**
     - none

TODO


@groupprefix
""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - ""

TODO


@groupNameExtractorRegex
""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - CN=(.*?)(?:,|$)

TODO


@style
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

Must be one of:

* AD - Active Directory
* DS - Unknown




@ldapSecurityType
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - simple

Binding to ldap server. One of either

* none
* simple


@serviceAccountDN
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO Confirm

Service account for binding to ldap server

e.g. CN=servicename,OU=serviceaccounts,DC=example,DC=local


@serviceAccountCredential
"""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO Confirm

Credential (password) assocaiated with serviceAccountDN


@groupObjectClass
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - strings
   * - **Default**
     - group

Name of LDAP class attached to group objects


@userObjectClass
""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO
   * - **Type**
     - TODO
   * - **Default**
     - TODO

TODO


@groupBaseRDN
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true
   * - **Type**
     - string
   * - **Default**
     - none

.. note::
  Requires confirmation

  Is this parth searchable

RDN to container containing group objects.

E.g. 

* DC=example,DC=local
* OU=groups,DC=example,DC=local


@userBaseRDN
""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

.. note::
  Requires confirmation

  Is this parth searchable

RDN to container containing user objects.

E.g. 

* DC=example,DC=local
* OU=users,DC=example,DC=local


@x509groups
"""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO


@x509addAnonymous
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@matchGroupInChain
""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@nestedGroupLookup
""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO  confirm

Follow nested groups


@postMissionEventsAsPublic
""""""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@ldapsTruststore
""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO


@ldapsTruststoreFile
""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

Path to trust store containing certificate used to verify LDAP
server connection certificate.


@ldapsTruststorePass
""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

The password associcated with keystore in @ldapsTruststoreFile


@readOnlyGroup
""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO


@readGroupSuffix
""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - _READ

TODO


@writeGroupSuffix
"""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - _WRITE

TODO


@loginWithEmail
"""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@callsignAttribute
""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO


@colorAttribute
"""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO


@roleAttribute
""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - none

TODO


@enableConnectionPool
"""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@connectionPoolTimeout
""""""""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - 30000

TODO


@dnAttributeName
""""""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - distinguishedName

TODO


@nameAttr
"""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - cn

TODO

<File>
^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

Configures file based user authentication. Usually using
UserAuthenticationFile.xml

@location
"""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - UserAuthenticationFile.xml

Path to the file used for authentication relative to the root of the tak server
deployment

<oauth>
^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO


@default
^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - file

TODO


@DNUsernameExtractorRegex
^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - string
   * - **Default**
     - CN=(.*?)(?:,|$)

TODO


@x509groups
^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO


@x509groupsDefaultRDN
^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@x509addAnonymous
^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@x509useGroupCache
^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@x509useGroupCacheRequiresExtKeyUsage
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - true

TODO


@x509checkRevocation
^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@x509tokenAuth
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO





<submission>
------------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

Submission service configuration

@ignoreStaleMessages
^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - none

TODO

@validateXml
^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO


@dropMesssagesIfAnyServiceIsFull
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO



<subscription>
--------------

Subscriptions

@reloadPersistent
^^^^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false
   * - **Type**
     - boolean
   * - **Default**
     - false

TODO

<static>
^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true

Defines static subscriptions

<filtergroup>
"""""""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO


<filter>
""""""""

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - false

TODO




<repository>
------------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - true

Database configuration

<repeater>
----------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO

<filter>
--------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<buffer>
--------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<dissemination>
---------------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<certificateSigning>
--------------------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<logging>
---------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<security>
----------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<ferry>
-------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<async>
-------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<federation>
------------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<geocache>
----------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<citrap>
--------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<xmpp>
------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<plugins>
---------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<cluster>
---------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<docs>
------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<email>
-------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<locate>
--------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<vbm>
-----

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO


<profile>
---------

.. list-table::
   :widths: 25 75
   :header-rows: 0

   * - **Required**
     - TODO
