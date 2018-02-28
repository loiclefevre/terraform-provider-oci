    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***
# v2.1.0 release
The `v2.1.0` release is a significant update to the OCI Terraform Provider.

As part of this release, we fixed some bugs along the way.

#### Fixes
The following is the list of changes -

- `display_name` in `oci_core_volume_attachment` resource is now set to `forceNew`. It was never mutable in the first place, we just made it explicit

- Ensured that the keys are always in lower-case in the `metadata` map in `oci_objectstorage_object` resource

- All the fields in `oci_objectstorage_preauthrequest` are now `forceNew` (they were not earlier). This resource does not support updates.

## OCI resource and datasource details
[comment]: <> (TODO: Fix docs link before release)
https://github.com/oracle/terraform-provider-oci/tree/preview/docs

## Getting help
You can file an issue against the project
https://github.com/oracle/terraform-provider-oci/issues

## Known issues
[Github issues](https://github.com/oracle/terraform-provider-oci/issues)

