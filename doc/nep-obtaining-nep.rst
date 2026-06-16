.. _nep-obtaining-nep:

***************
 Obtaining NEP
***************

As described at :ref:`Online Resources<nep-online-resources>`, NetEye Extension Packs can be obtained through two main channels:

* Wuerth Phoenix's RPM Repository ``neteye-contrib``
* NEP's Repository on GitHub

Wuerth Phoenix's RPM Repository ``neteye-contrib`` is *the official channel*: through it, all the Official Stable Versions of NEP are made available via RPM package. Those RPMs will have the sole duty of making all necessary contents available for installation, allowing the End User to import only the strictly required objects. Each version of NetEye will come with its set of compatible NEPs packed inside the proper RPM. This channel is freely accessible by all Wuerth Phoenix's Customers.

NEP's Repository on GitHub is *the development channel*: through it, it is possible to get the contents of all stable versions of NEP as well as the current development release. This makes possible for everyone to get NEP freely. Also, if anyone desires it, everyone can contribute to the development of the project.
Even if NEPs have NetEye as their target platform, they can be used on any system that equips the same underlying software a NetEye system.

Please note that just downloading and installing these files will not automatically deploy all NEP's contents into NetEye: it is up to the End User to perform the import of one or more Packages by manually performing the Package Setup. This allows for a system to have the smallest footprint, enabling an easier management of the NEP-related Objects. Therefore, each NEP comes with a setup procedure that must be run by the end user before all objects become usable. Additionally, the setup procedure can be re-executed to restore all the objects to their original state.

.. _nep-obtaining-nep-external-repos:

Enable access to external repos
===============================

NetEye Extension Packs requires access to external resources to complete the setup. Without these resources, the install/update procedure for some NEPs might fail.
Therefore, you must ensure your NetEye Servers have access to these websites:

* repo.wuerth-phoenix.com
* linux.dell.com
* grafana.com
* yum.centreon.com
* yum-gpg.centreon.com
* github.com

In case your NetEye has the SIEM Module, ensure all your NteEye Servers have access also to these websites:

Only for NetEye SIEM:

* epr.elastic.co
* geoip.elastic.co
* storage.googleapis.com


Installing from RPM Repository
==============================

Installing NetEye Extension Packs from Wuerth Phoenix's RPM Repository is fairly simple: just install the NEP RPM provided by the repository on the required NetEye Systems:

* If you have a NetEye Single-Node deployment, install the RPM on the Single-Node NetEye
* If you have a NetEye Cluster deployment, install the RPM on all Cluster Nodes

To install the NEP RPM, just run this line of code in a shell with ``root`` privileges:

.. code:: bash

    yum -y --enablerepo=neteye-contrib install neteye-nep

After this procedure, all NEP's related contents will be available at ``/usr/share/neteye/nep`` directory, that will become your NEP Content's Source.


Installing from NEP's Public GitHub Repository
==============================================

.. warning:: Use of GitHub Repository is strongly discouraged for production environment. Production environment should be managed only via RPM from our official repositories.
    While contents provided by the Master Branch are still complete and stable, they should not be considered as a stable release.
    GitHub Repo should be used only for testing purposes only or for preparing your own contribution to NEP Project.

Installing NetEye Extension Packs from NEP's public GitHub Repository is just like cloning a GitHub Repository: just clone the NEP Repository on the required NetEye Systems:

* If you have a NetEye Single-Node deployment, clone it on the Single-Node NetEye
* If you have a NetEye Cluster deployment, clone it on all Cluster Nodes

Before cloning, find a suitable path to where clone NEP Repository contents. For the sake of simplicity, it is possible to assume ``/usr/share/neteye/`` as a suitable path.
To clone the NEP Repository from GitHub, just run these commands in a shell with ``root`` privileges:

.. code:: bash

    mkdir -p /usr/share/neteye/nep
    git clone https://github.com/neteye-platform/nep.git /usr/share/neteye/nep
    mkdir -p /neteye/shared/nep/data/packages
    ln -s /usr/share/neteye/nep/setup/nep-setup /usr/sbin/nep-setup

After this procedure, all NEP's related contents will be available at ``/usr/share/neteye/nep`` directory, that will become your NEP Content's Source.
