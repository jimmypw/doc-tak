CoreConfig.xml
==============

The CoreConfig.xml file is the primary configuration file. It is written in xml
and it is read from various TAKserver processes to retrieve the configuration
that is relevant to it.

The options in this file have been interpreted from CoreConfig.xsd which is the 
XSD schema that validates the corresponding XML file. The functionality
associated with the configuration directive is either known or is still yet to
be deciphered from reading the code.

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

Group name associated with the input


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

Host insterface name to listen on

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

TODO


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
