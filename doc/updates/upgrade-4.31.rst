.. _nep_updates_upgrade_4_31:


***************************************
 Upgrade to NetEye 4.31
***************************************

With the release of NetEye 4.31, we introduced a new version of out provisioning tool, namely ``nep-setup``. This tool has been completely rewritten to improve its stability and global performance, but together with it we had to perform some changes in all NEP configuration files. If your NetEye is using NEP provided for NetEye 4.30 or older, you must see the following instructions to migrate older data to the newer version required by ``nep-setup`` for Neteye 4.31.


Understand the migration
========================
During its lifetime, ``nep-setup`` stores the data it processes in a dedicated directory. Data in this path must be fully compatible with the newer version of ``nep-setup`` in order for it to perform it works. Contents of this directory are stored using a structure that closely reflects data from NEP configuration files. Therefore, all contents of this directory must be upgraded accordingly to allow the new version of ``nep-setup`` to operate.
The path of this directory is ``/neteye/shared/nep/data/packages/``.


Understand if you need to migrate
=================================
To understand if you need to perform the migration, look at the contents of directory ``/neteye/shared/nep/data/packages/`` on your NetEye Master: if this directory is empty, migration process is not needed and can be skipped.

Check a Single Node deployment
------------------------------
To check if a NetEye Single Node needs to be migrated, just list contents of directory ``/neteye/shared/nep/data/packages/``: if the directory is not empty, it must be migrated.

.. code:: bash

    # This NetEye needs to be migrated
    [root@neteye-single-node ~]# ls -1 /neteye/shared/nep/data/packages/
    nep-common
    nep-monitoring-asset
    nep-monitoring-core
    nep-monitoring-siem
    [root@neteye-single-node ~]#


Check a Cluster deployment
--------------------------
To check if a NetEye Cluster needs to be migrated, just list contents of directory ``/neteye/shared/nep/data/packages/`` on the node where resource ``nep_drbd_fs`` is running: if the directory is not empty, it must be migrated.

.. code:: bash

    # This NetEye Cluster needs to be migrated
    [root@node1 ~]# pcs resource | grep nep_drbd_fs
        * nep_drbd_fs       (ocf::heartbeat:Filesystem):     Started node2.neteyelocal
    [root@node1 ~]# ssh node2.neteyelocal ls -1 /neteye/shared/nep/data/packages/
    nep-common
    nep-monitoring-asset
    nep-monitoring-core
    nep-monitoring-siem
    [root@node1 ~]#


Run the migration
=================
Migration process is managed by a migration script. The migration script can be executed as many times as you want: it will only take care of what needs to be migrated. Migrated content is left as it is. The migration script is ``/usr/share/neteye/nep/setup/migration/migrate-nep-data.sh``.


Migrate a NetEye Single Node
----------------------------
To migrate contents on a NetEye Single Node, just run the migration script.

.. code:: bash

    [root@neteye-single-node ~]# bash /usr/share/neteye/nep/setup/migration/migrate-nep-data.sh
    Converting prerequisite files of installed NEPs
    Done. Converting installed NEP directory tree...
    Renaming: /neteye/shared/nep/data/packages/nep-common/v.5 -> /neteye/shared/nep/data/packages/nep-common/0.0.5
    Renaming: /neteye/shared/nep/data/packages/nep-common/v.6 -> /neteye/shared/nep/data/packages/nep-common/0.0.6
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-core/v.8 -> /neteye/shared/nep/data/packages/nep-monitoring-core/0.0.8
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-siem/v.7 -> /neteye/shared/nep/data/packages/nep-monitoring-siem/0.0.7
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-asset/v.4 -> /neteye/shared/nep/data/packages/nep-monitoring-asset/0.0.4
    [root@neteye-single-node ~]#


Migrate a NetEye Cluster
------------------------
To migrate contents on a NetEye Cluster, just run the migration script in the node where resource ``nep_drbd_fs`` is running. Otherwise, just run it on all cluster nodes.

.. code:: bash

    [root@neteye-single-node ~]# bash /usr/share/neteye/nep/setup/migration/migrate-nep-data.sh
    Converting prerequisite files of installed NEPs
    Done. Converting installed NEP directory tree...
    Renaming: /neteye/shared/nep/data/packages/nep-common/v.5 -> /neteye/shared/nep/data/packages/nep-common/0.0.5
    Renaming: /neteye/shared/nep/data/packages/nep-common/v.6 -> /neteye/shared/nep/data/packages/nep-common/0.0.6
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-core/v.8 -> /neteye/shared/nep/data/packages/nep-monitoring-core/0.0.8
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-siem/v.7 -> /neteye/shared/nep/data/packages/nep-monitoring-siem/0.0.7
    Renaming: /neteye/shared/nep/data/packages/nep-monitoring-asset/v.4 -> /neteye/shared/nep/data/packages/nep-monitoring-asset/0.0.4
    [root@neteye-single-node ~]#


Post-migration steps
====================
After the migration is done, you can check ``nep-setup`` is working properly by listing all available contents. Then, as usual, you have to upgrade all the installed NEPs to the latest version available.


Notes about NEP Setup
=====================
Command line changes slightly. Just run ``nep-setup --help`` to look at all the available arguments. The new ``nep-setup`` is not much talkative. You should enable base logging for all steps. To do so, add ``-v`` to the command line. If you prefer a more verbose logging, use ``-vv`` instead.
