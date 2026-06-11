.. _nep_advanced:


*****************
 Advanced Topics
*****************

NEP distribution logic
======================
A NetEye Extension Pack (NEP) is essentially a way to create objects inside NetEye. It consists of several configuration items that describe the creation process for each object. These objects are not created during the installation and configuration of the NEP itself: the end user must decide when to create or update the related NetEye objects. This will prevent collateral damage due to automated setup/upgrade processes, allowing the end user to prepare for the upgrade process.

An NEP can be imported immediately, or it may depend on one or more NEPs, which means that it may require one or more other NEPs to be installed first. After being imported, all the provided objects are available for use almost out of the box (in general, only minimal or zero configuration is required).

As stated above, an NEP may require one or more other NEP Packages to be installed before being installable. In fact, all packages create a tree-like structure where each NEP extends that tree with its own objects. This structure reduces the number of unused objects to a minimum, resulting in a smaller footprint for the whole design.


What can be shipped with an NEP
===============================
The latest revision of the NEP Package provides support for:

* Definitions of Monitoring Objects (in the form of Director Objects)
* ITOA Dashboards
* Configuration elements
* Monitoring Plugins
* Custom scripts

Although not officially supported, NEPs can still provide other kinds of objects.


Package structure
=================
An NEP Package is a method of distribution. It is versioned, and each version has a specific structure, allowing specific *extension* contents to be distributed. While a number of extension contents are supported by a specific package version, the package itself can contain objects that are originally not expected as custom (optional) contents. The package can also contain optional scripts to run before and after the main setup phase. Each NEP is packed inside one or more RPM files available through Wuerth Phoenix Repositories.


Latest Pack structure
---------------------
Here is the structure for the latest version of the NEP Package:

.. code-block:: bash

    Package v0.1
    ├───prerequisites.txt
    ├───prerequisites.ini
    ├───baskets
    │   ├───import
    │   └───import_once
    ├───plugins
    ├───custom_files
    │   ├───system_root
    │   ├───neteye_local_root
    │   └───neteye_shared_root
    │       └───icinga2
    │           ├───conf
    │           └───data
    ├───itoa
    ├───doc
    └───setup_scripts
        ├───pre
        └───post

The current version can accommodate:

- Director Baskets
- ITOA Dashboards
- Monitoring Plugins
- Configuration files for NetEye (Shared and Local)
- Optional pre-setup scripts
- Optional post-setup scripts
- Documentation


NEP contents logic
==================
Objects imported from NEPs are supposed to be immutable: in general, they should not be edited or changed. Of course some exceptions are allowed, but the fundamental idea is that what has been imported from an NEP can be changed only by the NEP itself. If an object coming from a NEP has to be edited, it must be cloned into a new one.

This approach supports an easy update procedure in case a newer version of the same NEP is released. Also, in the case of unrecoverable changes, all NEP objects can be recreated without fear of losing their customizations.
