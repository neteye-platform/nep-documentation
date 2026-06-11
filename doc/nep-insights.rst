**************
 Insights
**************

Extension contents
==================
Each NEP Package contains the content that can be used to build the required NetEye design. The main Extension contents shipped with a package are:

* Director Objects
* ITOA Dashboards
* Configuration elements
* Monitoring Plugins

Most of these can be used without any particular limitations: an ITOA Dashboard can be opened right after its import, and both Configuration elements and Monitoring Plugins can be used immediately after placing them in the right path. Instead, Director Objects require a well-defined set of rules and best practices to be used efficiently.


Director Objects
================
Director Objects are the inner core of the entire solution. Their objective is to provide easy-to-use monitoring object definitions. Each object comes with ample support for its configuration and are organized in structures that can provide a basic and meaningful (in other words, standard) monitoring for hosts or devices. This way, there is a basic set of variables and performance data that all the other Extension contents can use to build their functionalities upon.

To ensure this, Director Objects have to be organized in self-containing blocks that can be combined preserving each own identities, data and structure. This lead to the concept of ``Template-Types``.


What is a Template-Type
-----------------------
A ``Template-Type`` is a Template that defines a specific *purpose*, selecting which variables are required to ensure its purpose is completely fulfilled, and isolating them from other Template-Types. The *purpose* is a part of the monitored object that needs to be defined, like the kind of monitoring, how this monitoring can be done, whether or not it can be managed by a Cluster Zone, and so on. In short, a ``Template-Type`` selects an aspect of a monitored object (which can be Host or Service) and defines all the data that is needed to describe this aspect, ensuring no other Template-Type will redefine/rewrite that data.

Remember that, excluding some exceptions, objects provided by an NEP should not be edited directly: in case of an update or restore operation, all editing will be lost. If a Template must be edited, create a Child template and make any changes there.


Template-Types for Hosts
------------------------
Template-Types have been defined for both Hosts and Services. While their names are similar, their purpose and use are not exactly the same. The next table summarizes the available Template-Types for Host Objects.

=============== ===================== ===========
Template-Type   Host Template Name    Description
=============== ===================== ===========
Host Status     nx-ht-type-status     Defines the way the state of the host is probed
Host Monitoring nx-ht-type-monitor    Describes how a specific technology should be monitored by providing the required Services, Data Fields and Custom Variables
Host Location   nx-ht-type-location   Implements the concept of distributed objects with both logical position (Icinga Cluster Zones) and geographical position (address, coordinates, etc.)
Host Custom     nx-ht-type-custom     Used to overwrite Custom Variables coming from other Templates, as well as to alter Check Execution parameters, for a specific set of objects; it also provides default Check Command and Check Execution parameters to all monitored Host Objects
=============== ===================== ===========

Each ``Template-Type`` defines and provides the (custom) variables strictly required to perform its monitoring duty. As an example, a ``Template-Type`` *Host Monitoring* is not supposed to define a ``Cluster Zone``: it is not its duty to decide the Icinga Cluster Zone where it should be managed; instead, this information must be set by ``Template-Type`` *Host Location*. For the same reason, a ``Template-Type`` Host Location is not supposed to provide values for ``Icinga2 Agent`` and related, because it is a specific setting required for monitoring purposes. By enforcing this rule, each template can be considered a sealed box, and then all Host Objects can be created by combining different Template Types.


Template-Type: Host Status
~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Host Status* aim to define how the state of a Host Object is monitored. The main parameter provided is ``Check command``, but also all the Check Execution settings must be defined using this kind of template. In fact, to ensure all Host Objects are monitored using consistent parameters, it is better to provide them with the required settings using a dedicated template instead of relying on the settings used on a multitude of *Host Monitoring* Templates. This is the main reason that a Host Object must be created by using one (or more) template of type *Host Monitoring* and one template of type *Host Status*.

All Host Objects defined by Automations provided by NEPs automatically include the specific nx-ht-status-ping template dispatched with ``nep-common``.


Template-Type: Host Monitoring
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Host Monitoring* have the purpose of implementing a well-defined monitoring strategy for a specific technology. Each of them contains all and only those required Data Fields to configure its settings, allowing for a complete monitoring configuration at the Host Object level. That data will be used automatically by the necessary Service Objects to monitor performance and all other aspects of the same technology on that very Host Object.

All technologies are grouped into categories, with each one designed to build a hierarchy together with the others. As the concept of hierarchy implies, technologies will have more similar behaviors and settings the closer they are to each other in the hierarchy tree. This allows for quick and easy understanding of what and how an object will be monitored. Also, the design of the categories and their naming enables an intuitive way to look up for the required type of monitoring.

Templates of type *Host Monitoring* usually don't provide info about how the state of a Host Object is monitored: their aim is to provide Service Objects with all the data they might require to work. Parameters like ``Check command``, ``Check Interval``, ``Retry Interval`` and ``Check Attempts`` are managed using templates of type *Host Status* or using type *Host Custom*.


Template-Type: Host Location
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Host Location* are meant for providing settings and information about the actual location of the monitored Host Objects both in terms of physical location (address or position) and monitoring location (Icinga Cluster Zone). Data provided through this kind of template is useful to group Host Objects or to restrict their access on a geographical or logical basis.

Because there is actually no standard for coding geographical or positioning data, it is the responsibility of the end user to create as many *Host Location* templates as he/she desires with the Data Fields that better describe its scenario.

As stated above, the use of templates of type *Host Location* is *optional* and not strictly required to build a working monitoring design.


Template-Type: Host Custom
~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Host Custom* are used to provide Host Objects having common characteristics with the same set of (Custom) Variables. Therefore, their main purpose is to overwrite settings of Host Templates in case the default values provided by the other templates are wrong. Because Host Objects with common characteristics will have the same set of overwritten variables, templates of type *Host Custom* are also suitable to group together Host Objects and clarify the structure of the end user's infrastructure (e.g.: intranet servers, backup servers, core network devices, virtualization infrastructure etc.) They will thus become useful for managing Host Groups and user account authorization.

All Host Objects defined by Automations provided by NEPs automatically include the default *Host Custom* template dispatched with ``nep-common``.


Template-Types for Services
---------------------------
The next table summarizes the available Template-Types for Service Objects. While the names are similar, Template-Types for Services behave slightly different from those for Hosts.

================== ===================== ===========
Template-Type      Service Template Name Description
================== ===================== ===========
Service Monitoring nx-st-type-monitor    Describes how a specific aspect of a technology should be monitored
Service Custom     nx-st-type-custom     Used to overwrite Custom Variables coming from other Templates, as well as to alter Check Execution parameters, for a specific set of objects
================== ===================== ===========

Each ``Template-Type`` makes use of (Custom) Variables defined in its companion *Host Monitoring* Template, and allows for an override of these values directly at the Service Object level (if needed).


Template-Types: Service Monitoring
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Service Monitoring* implement a well-defined monitoring strategy for a given aspect of a specific technology. Each one has a companion HT of type *Host Monitoring* providing all the required (Custom) Variables to perform its monitoring duty. If for some reason, one or more Variables coming from the companion HT must be replaced, each ST provides full support for override and redefinitions.

Like HTs of type *Host Monitoring*, all STs of type *Service Monitoring* are grouped into categories designed to build a hierarchy.
Unlike HTs of type *Host Monitoring*, all the STs of type Service Monitoring define default values for ``Check Command`` parameter. Parameters ``Check Interval``, ``Retry Interval`` and ``Check Attempts`` can be managed via *Service Custom* Templates if required.


Template-Types: Service Custom
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Templates of type *Service Custom* are used to manage ``Check Execution`` parameters and overwrite (Custom) Variables coming from other ST where it is needed. In case a Service Object needs different ``Check Execution`` parameters or it must be provided with other (Custom) Variables, this ``Template-Type`` can be used to perform this task.


How to create Objects using Template-Types
------------------------------------------
Creating Objects using ``Template-Types`` is quite simple. They can be viewed as building-blocks that can stick together in the right quantity. Some of them are mandatory, others can be used only if their functionalities are required. This means this paradigm relies heavily on **Multiple Inheritance**.

To create Host Objects, one Template of type *Host Custom*, one Template of type *Host Status* and one or more of type *Host Monitoring* are strictly required: the *Host Custom* type provides ``Check Execution`` parameters, the *Host Status* type provides the ``Check command``, while the *Host Monitoring* type provides the Data Fields that Service Objects can use. Host Objects created this way will be assigned to the Icinga Master Zone. If Distributed Monitoring is required, or if Host Objects needs to be classified by geographical or logical location data, **only one** Template of type *Host Location* can be used.

To be more specific, a Host Object must be built following these steps. To obtain the maximum advantage using this paradigm, be sure to import all the Templates in the displayed order.

* Add **one** HT of type Host Status
* Add **one or more** HT of type Host Monitoring
* Add **one** HT of type Host Location (*Optional*)
* Add **one** HT of type Host Custom

Like Host Objects, Service Objects must be built following these steps:

* Add **one** ST of type Service Monitoring
* Add **one** ST of type Service Custom

Because Service Templates of type *Service Monitoring* provide their own ``Check Command``, the use of type *Service Custom* is not strictly required. If not used, default values for ``Check Interval`` (5 minutes), ``Retry Interval`` (1 minute) and ``Check Attempts`` (3) will be used by Icinga 2. However, all Service Objects provided by Automations and Service Sets provided by NEPs automatically include the default *Service Custom* Template dispatched with ``nep-common``.

The outlined order is, for both Host Objects and Service Objects, the one that is used when designing an NEP Package, therefore it already includes the optimal behavior for each object. While each ``Template-Type`` acts as a sealed box, there might be cases when variables are managed by two different Template-Types. In this cases, since *Host Monitoring* Templates or *Service Monitoring* Templates must not be edited, inheritance order matters and can influence the final behavior significantly. Therefore, it is strongly suggested that you enforce the order outlined above for every created objects.


Predefined Service Sets
-----------------------
Basic monitoring for Host Objects is defined by grouping Templates of type *Service Monitoring* into Service Sets.
Those Service Sets will be assigned to Host Objects based on the *Host Monitoring* Templates used to create the Host Objects themselves,
and use default timings and settings provided by the default *Service Custom* Template. While this allows for easy and quick startup, it
might not be suitable over the long term. If settings for these Services (or the Services themselves) must be customized or replaced, it is
suggested to make use of the *Default NEP Service Set Disabling* function to exclude the whole Service Sets and make your own copy through cloning.
Then, you can freely customize the clone.


About custom Service Sets
-------------------------
Every time you create a clone of a Service Set provided by NEP, make sure to review the apply rule of the cloned template:
the default apply rule of a Service Set from NEP is built to implement Service Set exclusion based on the name of the Service
Set you cloned from, making your cloned Service Set non applied.
If you want to disable Service Set `nx-ss-generic-icinga-agent-state`, be sure to provide a Service Object that monitors the
status of the Icinga2 Agent running on all impacted Host Objects and name it `Icinga2 agent status`. This service is used by
some default NEP Dependencies that disables monitoring or notifications for agent-based Service Objects that rely on icinga2
Agent to perform the actual monitoring. If Service Object `Icinga2 agent status` is not present, several Dependency Apply Rules
will inevitabily generate errors, blocking Deploy from Director and Icinga2 Service Start/Restart.
