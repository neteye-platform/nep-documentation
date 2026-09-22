.. _nep_updates:


************************
 NEP Updates & Upgrades
************************

.. _nep_breaking_change_tenant_custom_variable:

Breaking Change: Tenant Custom Variable Migration
=================================================

Starting with the current NetEye and NEP upgrade path, the legacy NEP tenant
custom variable ``nx_neteye_tenant`` is no longer the reference used by NetEye features.
The supported tenant information is now stored in the host custom variable ``neteye_tenant``.

Before upgrading NEP components, verify every host where ``nx_neteye_tenant`` is defined
and ensure that ``neteye_tenant`` exists and contains the correct tenant value.

Note that this variable applies to host objects only and has no meaning on service objects.

This is a breaking change: features that depend on tenant information may not work correctly
after the upgrade if required host objects still rely solely on ``nx_neteye_tenant``,
or if ``neteye_tenant`` is missing or configured with an incorrect value.

After verifying that the new variable is working as expected in the upgraded environment,
you can remove the legacy ``nx_neteye_tenant`` variable from your host objects. This cleanup
is strongly recommended, though non-mandatory for the upgrade to proceed.

.. warning::

   This operation is **irreversible**. While it is not strictly mandatory, it is strongly
   recommended once you have verified that everything operates correctly after the upgrade.

After all NEPs have been upgraded, variable ``nx_neteye_tenant`` can be removed and its
contents wiped. To do so:

1. Log into NetEye.
2. In the main menu, select **Director**.
3. Scroll down the list of tiles and, under the section **"Do more with custom data"**, click on **Define Data Fields**.

   .. figure:: /nep/doc/img/define_data_field.png

4. Search for ``nx_neteye_tenant`` and click on it (refer to the **Field Name** column).

   .. figure:: /nep/doc/img/data_field_nx_neteye_tenant.png

5. Click on the **Delete** button.

   .. figure:: /nep/doc/img/modify_nx_neteye_tenant.png

6. In the confirmation dialog, set **Wipe related vars** to ``Yes``, then click **Delete** again to confirm.
7. If there are additional instances of the ``nx_neteye_tenant`` field, repeat steps 4–6 until all instances
   have been removed.
