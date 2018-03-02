    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***
# v2.1.0 release
The `v2.1.0` release is a significant update to the OCI Terraform Provider.

There were several major changes made under the hood.
But we have tried to minimize breaking changes on the surface in order to insulate our customers from too much churn.

[comment]: <> (TODO: Remove the following statement before release)
We are doing an beta release (`v2.1.0-beta`) for this version signaling our intent of minimizing customer impact in the face of big changes.

Please look at the documentation under this directory to see what facilities were [added](ADDED.md), which fields were [deprecated](DEPRECATED.md) and what bugs were [fixed](FIXED.md).

## General notice
In addition to the changes mentioned above, we are also issuing the following guidelines starting with this release.

#### Identity resources
The backend APIs for all `identity` resources actually require a `compartment_id` value to be passed in.
Currently, the APIs require the `OCID` of the `tenancy` to be passed in as the `compartment_id`.

However, introducing that requirement (of passing in `compartment_id`) with this release could have caused some backwards-incompatible changes.

Hence, with this release, we have added `compartment_id` as an optional field for the `Identity` resources.
If the Terraform configurations do not provide the `compartment_id`, the OCI Provider code uses the `OCID` of the `tenancy`, behind the scenes, to call the services.

We advise our users to start specifying the `compartment_id` in their Terraform configurations for their `identity` resources.

#### Computed fields
With this release, several fields in several resources have `optional=true` and `computed=true` set. These changes were driven by the backend API interfaces.

We want to draw attention to a consequence of this change. The following steps help explain what happens -

1. Don't specify a value to the optional field. Run `terraform apply` to create the resource.
2. The service assigns some default value, and returns it back to the client.
3. Being a computed field, this default value is saved the the Terraform state file.
4. Now add a value to the optional field in your Terraform configuration file, and apply.
5. Now resource is updated, and the Terraform state file is updated accordingly with the value you entered.
6. Now delete the optional field from your Terraform configuration, and do a `terraform plan`
7. No difference is detected.

This happens because of how the Terraform diff-ing algorithm works. Please be aware of this.



## OCI resource and datasource details
[comment]: <> (TODO: Fix docs link before release)
https://github.com/oracle/terraform-provider-oci/tree/preview/docs

## Getting help
You can file an issue against the project
https://github.com/oracle/terraform-provider-oci/issues

## Known issues
[Github issues](https://github.com/oracle/terraform-provider-oci/issues)

