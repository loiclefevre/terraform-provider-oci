    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***
# v2.1.0 release
The `v2.1.0` release is a significant update to the OCI Terraform Provider.

We are not introducing any backwards-incompatible change with this release.

However, some of the fields and functionality that we used to support and no longer supported by the backend APIs.
In addition, some of the fields have been renamed.

We are deprecating the fields that have been impacted by such backend API changes with this release.
The fields that are being deprecated should work as they did before.

However, in subsequent releases, these fields may be removed from the OCI Terraform Provider.  

#### Deprecated
The following is the list of fields that we are deprecating in the OCI Terraform Provider release.

- `time_modified` has been deprecated for the following resources -
  * oci_core_internet_gateway
  * oci_core_route_table  
  * oci_identity_compartment
  * oci_identity_group
  * oci_identity_policy
  * oci_identity_user

#### Soon to be deprecated
There are some fields that we did not deprecate in the current release.

However, these fields will be deprecated in subsequent releases because of changes made in the backend APIs.

The following are the fields that will be deprecated soon -

- `compartment_id` will be deprecated soon for the following. This field is currently ignored, if provided.
  * `oci_core_drg_attachment`
  * `oci_core_volume_attachment`
  * `oci_identity_user_group_membership`
  
- `image` in `oci_core_instance` will be deprecated once OCI Terraform Provider starts supporting `sourceDetails`.

## OCI resource and datasource details
[comment]: <> (TODO: Fix docs link before release)
https://github.com/oracle/terraform-provider-oci/tree/preview/docs

## Getting help
You can file an issue against the project
https://github.com/oracle/terraform-provider-oci/issues

## Known issues
[Github issues](https://github.com/oracle/terraform-provider-oci/issues)


