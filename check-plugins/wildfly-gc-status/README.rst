Check wildfly-gc-status
=======================

Overview
--------

This check plugin prints the garbage collector of a WildFly server, using its HTTP-JSON based API (JBossAS REST Management API). This allows us to monitor the application server without any additional configuration and installation - no need to deploy WAR-Agents like Jolokia. The plugin supports both standalone mode and domain mode.

Tested with WildFly 11 and WildFly 23.

To create a monitoring user, do this:

.. code-block:: bash

    /opt/wildfly/bin/add-user.sh 

.. code-block:: text

    What type of user do you wish to add? 
     a) Management User (mgmt-users.properties) 
     b) Application User (application-users.properties)
    (a): a

    Enter the details of the new user to add.
    Using realm 'ManagementRealm' as discovered from the existing property files.
    Username : wildfly-monitoring
    Password : 
    Re-enter Password : 
    What groups do you want this user to belong to? (Please enter a comma separated list, or leave blank for none)[  ]: 
    About to add user 'wildfly-monitoring' for realm 'ManagementRealm'
    Is this correct yes/no? yes
    Is this new user going to be used for one AS process to connect to another AS process? 
    e.g. for a slave host controller connecting to the master or for a Remoting connection for server to server Jakarta Enterprise Beans calls.
    yes/no? no


Fact Sheet
----------

.. csv-table::
    :widths: 30, 70
    
    "Check Plugin Download",                "https://github.com/Linuxfabrik/monitoring-plugins/tree/main/check-plugins/wildfly-gc-status"
    "Check Interval Recommendation",        "Once a minute"
    "Can be called without parameters",     "No"
    "Compiled for",                         "Linux, Windows"


Help
----

.. code-block:: text

    usage: wildfly-gc-status [-h] [-V] [--instance INSTANCE]
                             [--mode {standalone,domain}] [--node NODE] -p
                             PASSWORD [--timeout TIMEOUT] [--url URL] --username
                             USERNAME

    Prints the status of the Wildfly/JBossAS garbage collector.

    optional arguments:
      -h, --help            show this help message and exit
      -V, --version         show program's version number and exit
      --instance INSTANCE   The instance (server-config) to check if running in
                            domain mode.
      --mode {standalone,domain}
                            The mode the server is running.
      --node NODE           The node (host) if running in domain mode.
      -p PASSWORD, --password PASSWORD
                            WildFly API password.
      --timeout TIMEOUT     Network timeout in seconds. Default: 3 (seconds)
      --url URL             WildFly API URL. Default: http://localhost:9990
      --username USERNAME   WildFly API username. Default: wildfly-admin


Usage Examples
--------------

.. code-block:: bash

    ./wildfly-gc-status --username wildfly-monitoring --password password --url http://wildfly:9990

Output:

.. code-block:: text

    MarkSweepCompact: CollectionCount 2.0, CollectionTime 1s; Copy: CollectionCount 32.0, CollectionTime 4s


States
------

* Always returns OK.


Perfdata / Metrics
------------------

.. csv-table::
    :widths: 25, 15, 60
    :header-rows: 1
    
    Name,                                       Type,               Description                                           
    garbage-collector-<name>-collection-count,  Continous Counter,  The total number of collections that have occurred.
    garbage-collector-<name>-collection-time,   Milliseconds,       The approximate accumulated collection elapsed time in milliseconds.

<name> is the name of the garbage collector.


Credits, License
----------------

* Authors: `Linuxfabrik GmbH, Zurich <https://www.linuxfabrik.ch>`_
* License: The Unlicense, see `LICENSE file <https://unlicense.org/>`_.
