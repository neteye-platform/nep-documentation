*********************
 Introduction to NEP
*********************

NetEye helps you take care of several aspects of IT Service Management, from monitoring to log analysis and asset/resource management, with a free form approach. However, because of its wide range of features, building and maintaining an efficient design can become quite challenging:

* What's the best layout for arranging objects, reducing both the initial implementation effort and future management effort?
* Does the chosen strategy allow for easy management of each object's lifecycle?
* Can the chosen strategy easily and efficiently accommodate future growth, in terms of number of managed objects and of new functionalities?

Every day, we at Wuerth Phoenix deal with these questions, and our accumulated experience is then condensed into a common design that can be delivered to end users via modular packages, along with best practices and suggestions to get the most out of them. This enables:

* Fast implementation of an initial design
* The ability to include only the required components, keeping the design's footprint as small as possible
* A predefined approach to object creation and management, resulting in a clear understanding of the required effort for both
* A standard method to extend the design without breaking it, or causing conflicts with future upgrades/updates

This kind of logic not only applies to Monitoring, but also to all the other NetEye modules. In the end, this approach reduces the initial startup time and ongoing maintenance effort, resulting in a lower TCO for the whole solution itself.


What are NetEye Extension Packs?
================================
Essentially, a NetEye Extension Pack is the way Wuerth Phoenix delivers to end users all our accumulated NetEye experience in the form of a modular design. In short, it is the crystallization of all experience accumulated by Wuerth Phoenix in a specific field with NetEye, with an easy setup. It aims to build a new design for a fresh installation as fast as possible while keeping it in line with a standard that allows for easy management, extensibility and upgradeability. It can be used both within a brand new deployed NetEye infrastructure and can also be easily integrated into an existing setup.


The idea behind NEPs
====================
As mentioned above, the main idea is to make a brand new NetEye Infrastructure deployment ready to perform in the shortest time possible while keeping its setup as identical as possible to existing ones, maximizing reusability and standardizing the approach. To achieve this, some best practices and strong design rules had to be created and enforced to become the base of this design. The main driver is an easy and uniform user experience while designing and using NetEye, and second is a simple and neat approach to update procedures.


The fundamental unit: NEP Package
---------------------------------
The fundamental unit of NetEye Extension Pack is the Package itself: abbreviated NEP, it is a package containing everything needed to perform a specific duty. There is a base package that contains the foundation of the design, while all the other packages extend it. This means any package requires one or more other packages to be installed on the system itself in order to work as intended. The package containing the common foundation is called ``nep-common``.

All packages are based on NetEye and thus compatible with one specific version of it. This doesn't mean they are not usable outside a NetEye environment: with a little effort, a package can be installed on third-party systems as long as it uses the same open-source software contained into NetEye.

A NEP can ship a number of Extension contents of predefined type, providing support specific to them. Over time, this support will be extended, and the number of supported types will increase. Therefore, each NEP has a package version that describes which Extension contents are supported. To see the list of supported Extension contents, read more in the :ref:`nep_advanced` section.


Package management
------------------
For all NetEye-based setups, NEP provides a package management software that can perform all the basic tasks related to NEP maintenance. The tool is named ``nep-setup`` and can manage the three main operations required for package managements: install, reinstall and update.

With ``nep-setup`` is possible to view the list of installed packages and install the required ones. Also, in case a newer version of a Package is available on your system, it can also import the updated definitions.

In the unforeseen case that a change in some Director Object brokes the whole configuration, ``nep-setup`` is able to restore the currently installed version to its original state: if all objects follows the NE building rules, nothing will be lost.
