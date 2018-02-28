    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***
# v2.1.0 release
The `v2.1.0` release is a significant update to the OCI Terraform Provider.

The following is the list of features that were added to the OCI Terraform Provider.

# Filters
The filter functionality is documented [here](https://github.com/oracle/terraform-provider-oci/blob/master/docs/Filters.md).

#### Client-side filters
With this release, several data sources that did not support client-side filtering earlier, now support it.

The following is the list of data sources that support filtering starting with this release -

- `oci_database_databases`
- `oci_database_db_homes`
- `oci_database_db_nodes`
- `oci_database_db_system_shapes`
- `oci_database_db_systems`
- `oci_database_db_versions`
- `oci_identity_api_keys`
- `oci_load_balancer_backends`
- `oci_objectstorage_bucket_summaries`
- `oci_objectstorage_objects`

#### Server-side filter features
With the release, several data sources now support new server-side filter features.

The following are the changes to the filter functionality in some data sources -

- `state` field added to the following data sources -
  * `oci_core_dhcp_options`
  * `oci_core_images`
  * `oci_core_internet_gateways`
  
- `state` and `display_name` fields added to the following data sources-
  * `oci_core_route_tables`
  * `oci_core_security_lists`
  * `oci_core_subnets`
  * `oci_core_vcns` (legacy name: `oci_core_virtual_networks`)
  * `oci_core_volume_backups`
  * `oci_core_volumes`

- `db_system_shape` added to `oci_database_db_versions`

# New fields
One of the issues with the OCI Terraform Provider is that it did not support all the functionality exposed by the service APIs.
With this release, we have made progress towards getting to parity with the services that we currently support.

#### In resources
We added fields to several resources.

This will enable creating resources with more flexibility. This will also expand interpolation and output options.

The following are the changes in the resources -
- `oci_core_ipsec` now has the optional field `id`
- `oci_core_subnet` has a new computed field `subnet_domain_name`
- `oci_core_vnic_attachment` has a new optional and forceNew field `nic_index`
- `oci_core_virtual_network` now has computed field `vcn_domain_name`
- `oci_core_volume` now has computed field `is_hydrated`
- `oci_database_db_system` now has computed field `last_patch_history_entry_id`
- `oci_load_balancer_backend` now has computed field `name`
- `oci_objectstorage_bucket` now has computed fields `created_by`, `etag`, `time_created`
- `oci_objectstorage_preauthrequest` now has computed field `time_created`

#### In data sources
We added fields to several data sources as well.

This will enable newer fields to filter with. This will also make more fields available for interpolation.  

The following are the changes in some data sources -
- `oci_database_database` data source now has new field `db_backup_config`
- `oci_database_db_home` data source now has new field `last_patch_history_entry_id`
- `oci_database_db_node` data source now has new field `software_storage_size_in_gb`

#### New constraints
We have added some constraints to our resource definitions. These constraints were enforced by the services already.

This implies that some failures that we used see during the `apply` phase would be detected at the `plan` phase.

The following are the new client-side constraints -
- `route_rules` in `oci_core_route_table` now specifies the `MinItems` constraint (set to `0`)
- `security_list_ids` in `oci_core_subnet` now specifies the `MinItems` (`0`) and `MaxItems` (`5`) constraints
- `db_home` in `oci_database_db_system` now specifies the `MinItems` constraint (set to `1`)
- `statements` in `oci_identity_policy` now specifies the `MinItems` constraint (set to `1`)

## OCI resource and datasource details
[comment]: <> (TODO: Fix docs link before release)
https://github.com/oracle/terraform-provider-oci/tree/preview/docs

## Getting help
You can file an issue against the project
https://github.com/oracle/terraform-provider-oci/issues

## Known issues
[Github issues](https://github.com/oracle/terraform-provider-oci/issues)







