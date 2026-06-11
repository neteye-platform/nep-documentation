********************
 Available Packages
********************

NEP Packages are continuously updated: new features, new supported technologies and minor fixes will be released with almost every new version of NetEye. Here it's possible to view all the available packages, understanding which and how many packages are needed to deploy the required design for a specific NetEye Infrastructure setup.

List of available packages
==========================
This table describes all the available packages and their purposes, along with any dependencies. Remember that all packages besides ``nep-common`` requires ``nep-common``, so this requirement is not explicitly listed in the table.

.. |link-pre| raw:: html

    <a href="https://bitbucket.org/siwuerthphoenix/nep/src/maint-

.. |nep-common| raw:: html

    /nep-common/">nep-common</a>

.. |nep-notification-base| raw:: html

    /nep-notification-base/">nep-notification-base</a>

.. |nep-notification-email| raw:: html

    /nep-notification-email/">nep-notification-email</a>

.. |nep-notification-opsgenie| raw:: html

    /nep-notification-opsgenie/">nep-notification-opsgenie</a>

.. |nep-notification-msteams| raw:: html

    /nep-notification-msteams/">nep-notification-msteams</a>

.. |nep-notification-phonecall| raw:: html

    /nep-notification-phonecall/">nep-notification-phonecall</a>

.. |nep-notification-servicenow| raw:: html

    /nep-notification-servicenow/">nep-notification-servicenow</a>

.. |nep-notification-sms| raw:: html

    /nep-notification-sms/">nep-notification-sms</a>

.. |nep-notification-telegram| raw:: html

    /nep-notification-telegram/">nep-notification-telegram</a>

.. |nep-nrpe-base| raw:: html

    /nep-nrpe-base/">nep-nrpe-base</a>

.. |nep-windows-icinga-powershell-base| raw:: html

    /nep-windows-icinga-powershell-base/">nep-windows-icinga-powershell-base</a>

.. |nep-centreon-plugins-base| raw:: html

    /nep-centreon-plugins-base/">nep-centreon-plugins-base</a>

.. |nep-monitoring-core| raw:: html

    /nep-monitoring-core/">nep-monitoring-core</a>

.. |nep-monitoring-siem| raw:: html

    /nep-monitoring-siem/">nep-monitoring-siem</a>

.. |nep-monitoring-asset| raw:: html

    /nep-monitoring-asset/">nep-monitoring-asset</a>

.. |nep-monitoring-vmd| raw:: html

    /nep-monitoring-vmd/">nep-monitoring-vmd</a>

.. |nep-network-base| raw:: html

    /nep-network-base/">nep-network-base</a>

.. |nep-network-apc-netbotz| raw:: html

    /nep-network-apc-netbotz/">nep-network-apc-netbotz</a>

.. |nep-network-cisco-standard| raw:: html

    /nep-network-cisco-standard/">nep-network-cisco-standard</a>

.. |nep-network-cisco-wlc| raw:: html

    /nep-network-cisco-wlc/">nep-network-cisco-wlc</a>

.. |nep-network-dell-idrac| raw:: html

    /nep-network-dell-idrac/">nep-network-dell-idrac</a>

.. |nep-network-dell-switch| raw:: html

    /nep-network-dell-switch/">nep-network-dell-switch</a>

.. |nep-network-kemp-load-balancer| raw:: html

    /nep-network-kemp-load-balancer/">nep-network-kemp-load-balancer</a>

.. |nep-network-citrix-load-balancer| raw:: html

    /nep-network-citrix-load-balancer/">nep-network-citrix-load-balancer</a>

.. |nep-network-messpc-ethernetbox| raw:: html

    /nep-network-messpc-ethernetbox/">nep-network-messpc-ethernetbox</a>

.. |nep-network-checkpoint-firewall| raw:: html

    /nep-network-checkpoint-firewall/">nep-network-checkpoint-firewall</a>

.. |nep-network-paloalto-firewall| raw:: html

    /nep-network-paloalto-firewall/">nep-network-paloalto-firewall</a>

.. |nep-network-sophos-firewall| raw:: html

    /nep-network-sophos-firewall/">nep-network-sophos-firewall</a>

.. |nep-network-pfsense-firewall| raw:: html

    /nep-network-pfsense-firewall/">nep-network-pfsense-firewall</a>

.. |nep-network-ups| raw:: html

    /nep-network-ups/">nep-network-ups</a>

.. |nep-network-printer| raw:: html

    /nep-network-printer/">nep-network-printer</a>

.. |nep-vmware-api| raw:: html

    /nep-vmware-api/">nep-vmware-api</a>

.. |nep-vmware-vmd| raw:: html

    /nep-vmware-vmd/">nep-vmware-vmd</a>

.. |nep-dbms-base| raw:: html

    /nep-dbms-base/">nep-dbms-base</a>

.. |nep-database-oracle| raw:: html

    /nep-database-oracle/">nep-database-oracle</a>

.. |nep-server-dns| raw:: html

    /nep-server-dns/">nep-server-dns</a>

.. |nep-server-ntp| raw:: html

    /nep-server-ntp/">nep-server-ntp</a>

.. |nep-server-email| raw:: html

    /nep-server-email/">nep-server-email</a>

.. |nep-storage-base| raw:: html

    /nep-storage-base/">nep-storage-base</a>

.. |nep-storage-emc| raw:: html

    /nep-storage-emc/">nep-storage-emc</a>

.. |nep-storage-ibm| raw:: html

    /nep-storage-ibm/">nep-storage-ibm</a>

.. |nep-storage-netapp| raw:: html

    /nep-storage-netapp/">nep-storage-netapp</a>

.. |nep-storage-qnap| raw:: html

    /nep-storage-qnap/">nep-storage-qnap</a>

.. |nep-website| raw:: html

    /nep-website/">nep-website</a>

.. |nep-windows-active-directory| raw:: html

    /nep-windows-active-directory/">nep-windows-active-directory</a>

.. |nep-windows-server-exchange| raw:: html

    /nep-windows-server-exchange/">nep-windows-server-exchange</a>

.. |nep-alyvix| raw:: html

    /nep-alyvix/">nep-alyvix</a>

.. |nep-influxdb-query| raw:: html

    /nep-influxdb-query/">nep-influxdb-query</a>

.. |nep-windows-wsman| raw:: html

    /nep-windows-wsman/">nep-windows-wsman</a>

=============================================================================== =================================================================================================== ==================================
NEP Name                                                                        Description                                                                                         Required NEPs (besides nep-common)
=============================================================================== =================================================================================================== ==================================
|link-pre|\ |neteye_version|\ |nep-common|                                       Common base for all NEPs, provide basic monitoring capabilities
|link-pre|\ |neteye_version|\ |nep-notification-base|                            Facilities for a basic Icinga2 Notification management
|link-pre|\ |neteye_version|\ |nep-notification-email|                           Enable sending Icinga Notifications via EMail                                                       nep-notification-base
|link-pre|\ |neteye_version|\ |nep-notification-opsgenie|                        Enable sending Icinga Notifications via OPSGenie                                                    nep-notification-base
|link-pre|\ |neteye_version|\ |nep-notification-msteams|                         Enable sending Icinga Notifications via MSTeams                                                     nep-notification-base
|link-pre|\ |neteye_version|\ |nep-notification-phonecall|                       Enable sending Icinga Notifications via Phone Call (requires SMS Gateway)                           nep-notification-base, nep-notification-sms
|link-pre|\ |neteye_version|\ |nep-notification-servicenow|                      Enable sending Icinga Notifications via ServiveNow                                                  nep-notification-base
|link-pre|\ |neteye_version|\ |nep-notification-sms|                             Enable sending Icinga Notifications via SMS (requires SMS Gateway)                                  nep-notification-base
|link-pre|\ |neteye_version|\ |nep-notification-telegram|                        Enable sending Icinga Notifications via Telegram                                                    nep-notification-base
|link-pre|\ |neteye_version|\ |nep-nrpe-base|                                    Base checks for legacy systems with NRPE Agent
|link-pre|\ |neteye_version|\ |nep-windows-icinga-powershell-base|               Add support for Icinga PowerShell Plugins (directly from Icinga repo)
|link-pre|\ |neteye_version|\ |nep-centreon-plugins-base|                        Common base for all Centreon Plugins
|link-pre|\ |neteye_version|\ |nep-monitoring-core|                              Allow fast and precise monitoring of NetEye Health
|link-pre|\ |neteye_version|\ |nep-monitoring-siem|                              Add-on for NetEye Self Monitoring to monitor the SIEM Module                                        nep-monitoring-core
|link-pre|\ |neteye_version|\ |nep-monitoring-asset|                             Add-on for NetEye Self Monitoring to monitor the Asset Module                                       nep-monitoring-core
|link-pre|\ |neteye_version|\ |nep-monitoring-vmd|                               Add-on for NetEye Self Monitoring to monitor the VMD Module                                         nep-monitoring-core
|link-pre|\ |neteye_version|\ |nep-network-base|                                 Basic tools for advanced network monitoring via SNMP
|link-pre|\ |neteye_version|\ |nep-network-apc-netbotz|                          Specific monitoring for APC Netbotx                                                                 nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-cisco-standard|                       Specific monitoring for Cisco Standard via SNMP                                                     nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-cisco-wlc|                            Specific monitoring for Cisco WLC Controller                                                        nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-dell-idrac|                           Specific monitoring for Dell iDRAC via SNMP                                                         nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-dell-switch|                          Specific monitoring for Dell Switch via SNMP                                                        nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-citrix-load-balancer|                 Specific monitoring for Citrix Load Balancer via SNMP                                               nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-kemp-load-balancer|                   Specific monitoring for Kemp Load Balancer via SNMP                                                 nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-messpc-ethernetbox|                   Specific monitoring for MessPC EthernetBox sensors                                                  nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-checkpoint-firewall|                  Specific monitoring for Checkpoint Firewall via SNMP                                                nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-paloalto-firewall|                    Specific monitoring for PaloAlto Firewall via SNMP                                                  nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-sophos-firewall|                      Specific monitoring for Sophos Firewall via SNMP                                                    nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-pfsense-firewall|                     Specific monitoring for PfSense Firewall via SNMP                                                   nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-network-printer|                              Specific monitoring for Printers via SNMP                                                           nep-network-base
|link-pre|\ |neteye_version|\ |nep-network-ups|                                  Specific monitoring for UPS via SNMP                                                                nep-network-base
|link-pre|\ |neteye_version|\ |nep-vmware-api|                                   Monitoring for VMware Infrastructure through API
|link-pre|\ |neteye_version|\ |nep-vmware-vmd|                                   Monitoring for VMware Infrastructure through NetEye VMD Module                                      nep-vmware-api
|link-pre|\ |neteye_version|\ |nep-dbms-base|                                    Base monitoring for DBMS Server, DBMS Instances and Databases
|link-pre|\ |neteye_version|\ |nep-database-oracle|                              Provide basic tools to monitor Oracle-based Databases
|link-pre|\ |neteye_version|\ |nep-server-dns|                                   Monitoring for Server DNS (both Windows and Linux)
|link-pre|\ |neteye_version|\ |nep-server-ntp|                                   Monitoring for Server NTP (both Windows and Linux)
|link-pre|\ |neteye_version|\ |nep-server-email|                                 Provides the minimum requirements to implement a monitoring of Email Server
|link-pre|\ |neteye_version|\ |nep-storage-base|                                 Common base for all Storage monitoring Plugins
|link-pre|\ |neteye_version|\ |nep-storage-emc|                                  Specific monitoring for Storage EMC via SNMP                                                        nep-network-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-storage-ibm|                                  Specific monitoring for Storage IBM via Cli                                                         nep-network-base, nep-storage-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-storage-netapp|                               Specific monitoring for Storage NetApp via RestAPI and SNMP                                         nep-network-base, nep-storage-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-storage-qnap|                                 Specific monitoring for Storage QNAP via SNMP                                                       nep-network-base, nep-storage-base, nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-website|                                      Allows basic monitoring of HTTP/HTTPS Websites
|link-pre|\ |neteye_version|\ |nep-windows-active-directory|                     Monitoring for Windows Active Directory
|link-pre|\ |neteye_version|\ |nep-windows-server-exchange|                      Monitoring for Windows Server Exchange
|link-pre|\ |neteye_version|\ |nep-alyvix|                                       Monitoring for Alyvix Server
|link-pre|\ |neteye_version|\ |nep-influxdb-query|                               Allows monitoring through Real Time metrics gathered into InfluxDB OSS                              nep-centreon-plugins-base
|link-pre|\ |neteye_version|\ |nep-windows-wsman|                                Provides the monitoring of Microsoft Windows operating system using WSMAN                           nep-centreon-plugins-base
=============================================================================== =================================================================================================== ==================================


Package graph
=============
This graph shows via a graphical view the dependencies between each NEP Package.

.. todo::
    Replace this with an image!!

.. code-block:: bash

    nep-common
    ├───nep-notification-base
    |   ├───nep-notification-email
    |   ├───nep-notification-opsgenie
    |   ├───nep-notification-msteams
    |   ├───nep-notification-sms
    |   ├───nep-notification-servicenow
    |   ├───nep-notification-telegram
    |   └───nep-notification-phonecall
    ├───nep-windows-icinga-powershell-base
    ├───nep-centreon-plugins-base
    |   ├───nep-network-cisco-standard
    |   ├───nep-influxdb-query
    |   ├───nep-network-dell-switch
    |   ├───nep-network-citrix-load-balancer
    |   ├───nep-network-kemp-load-balancer
    |   ├───nep-network-paloalto-firewall
    |   ├───nep-network-pfsense-firewall
    |   ├───nep-storage-emc
    |   ├───nep-storage-ibm
    |   ├───nep-storage-netapp
    |   ├───nep-storage-qnap
    |   └───nep-windows-wsman
    ├───nep-monitoring-core
    |   ├───nep-monitoring-siem
    |   ├───nep-monitoring-vmd
    |   └───nep-monitoring-asset
    ├───nep-network-base
    |   ├───nep-network-apc-netbotz
    |   ├───nep-network-cisco-standard
    |   ├───nep-network-cisco-wlc
    |   ├───nep-network-dell-idrac
    |   ├───nep-network-dell-switch
    |   ├───nep-network-checkpoint-firewall
    |   ├───nep-network-citrix-load-balancer
    |   ├───nep-network-kemp-load-balancer
    |   ├───nep-network-messpc-ethernetbox
    |   ├───nep-network-sophos-firewall
    |   ├───nep-network-pfsense-firewall
    |   ├───nep-network-paloalto-firewall
    |   ├───nep-network-printer
    |   └───nep-network-ups
    ├───nep-vmware-api
    |   └───nep-vmware-vmd
    ├───nep-dbms-base
    ├───nep-database-oracle
    ├───nep-server-dns
    ├───nep-server-ntp
    ├───nep-server-email
    ├───nep-storage-base
    |   ├───nep-storage-emc
    |   ├───nep-storage-ibm
    |   ├───nep-storage-netapp
    |   └───nep-storage-qnap
    ├───nep-website
    ├───nep-windows-active-directory
    ├───nep-windows-server-exchange
    └───nep-alyvix
