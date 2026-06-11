Upgrade to NetEye 4.48
================================

With NetEye 4.48 IDO will be officially removed from your NetEye without further ado.

This obviously has some impact on NetEye Extension Packs as well: ``nep-common`` and ``nep-monitoring-core`` make use of Icinga IDO in different ways, so if you have them installed on your NetEye you should do some cleanup before actually upgrading the system to version 4.48.

Do I have to do something before upgrading?
--------------------------------------------

If you're reading this, you'll most likely have to. To be really sure, you have to check if NEP is installed on your NetEye and if you're using either ``nep-common`` or ``nep-monitoring-core``. You can use ``nep-setup list`` to see the list of installed NEPs: If the command exists and one or both NEPs are reported in the output, you will in fact have a few things to do.

How to fix ``nep-common``
--------------------------

.. note::

   **This is not blocking for the upgrade procedure, you can fix it after the upgrade.**

NEP ``nep-common`` provides a Grafana data source that can be used by dashboards to get data from the Icinga IDO Database. This data source is stored in Main Org., is of type ``mysql`` and is named ``mysql-icinga``. This data source poses no harm to anything, but after upgrading NetEye to 4.48, the underlying database will no longer be updated. So all dashboards using this data source will stop displaying updated data.

You'll have to take corrective actions **after the Upgrade**:

- Upgrade NEP to the latest release of NetEye 4.48; this will provide a new Grafana data source that allows access to the IcingaDB DB (its name is ``icingadb-mysql``)
- Update all dashboards to use this new data source; remember that the DB schema is completely different, so you'll also have to update all SQL statements
- Drop the data source ``icinga-mysql``

This procedure cannot be automated, but you can take advantage of some AI tools to get some help in translating the SQL queries to the new schema.

How to fix ``nep-monitoring-core``
-----------------------------------

.. warning::

   **If not done, neteye upgrade will not be allowed to run.**

NEP ``nep-monitoring-core`` actually monitors the status of the IDO connection. This configuration is no longer present on NEP for NetEye 4.48, but it's still used on NEP for NetEye 4.47. Again removal cannot be managed automatically, so you need to remove these items by yourself.

You have to:

1. Remove the Service Object that monitors IDO status
2. Remove the Service Template that monitors IDO status
3. Optionally, remove the Data Fields and Data Lists related to IDO Settings
4. Make sure to not update ``nep-monitoring-core`` before installing the latest version of NEP for NetEye 4.48

Everything has to be done in the NetEye Web UI, so make sure you are logged in with Administrative Privileges.

Remove the Service Object that monitors IDO status
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Go to Director and look for the Service Set ``nx-ss-neteye-icinga-instance-master-state``
2. Go to the Services tab and look for the Service ``Icinga IDO Performance``
3. Open the service, then delete it

Remove the Service Template that monitors IDO status
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Go to Director and look for Service Template ``nx-st-agent-icinga-ido-performance``
2. Ensure that this Service Template is not in use

   - If it is in use, follow the references and delete all services using it

3. Open the Service Template, then delete it

Remove the Data Fields and Data Lists related to IDO Settings (optional)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This step is not required since it's related to Director UI Elements, but it should be done to make everything neater.

1. Go to Director and open the *Data Fields* list
2. Look for all Data Fields having ``IDO`` in their name; you should see at least these Data Fields:

   - ``ido_name``
   - ``ido_type``
   - ``ido_pending_queries_critical``
   - ``ido_pending_queries_warning``
   - ``ido_queries_critical``
   - ``ido_queries_warning``

3. The Data Fields reported above should have no counters in the **# Used** and **# Vars** fields

   - If not, they are used elsewhere, and should not be removed, so skip this step

4. Delete each one of them
5. Move to the *Data lists* tab and look for Data List ``[NX] Icinga IDO Types List``
6. Edit it, then Delete it

Further remaining steps
~~~~~~~~~~~~~~~~~~~~~~~~

Now, you can check the integrity of your configuration by committing it with a Deploy. If everything is all right, Deploy should succeed. Now, you can proceed with the upgrade procedure. Make sure to run all Prerequisite Checks to ensure the safety of the whole procedure.

After the Upgrade is completed, as usual, update NEP RPM and then use ``nep-setup`` to update all required NEPs.
