# Datasource

- In Terraform, `data sources` let you read and use information from existing infrastructure or external systems without creating or modifying them.

<br />

![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765910240/4405d99f-6fce-4bba-a3d0-298a8bf8557c.png)

<br />

A data source:
- Fetches data from a provider (`AWS`, `Azure`, `GCP`, etc.)
- Does not create or manage resources
- Is evaluated during terraform plan and terraform apply
- Is referenced elsewhere in your configuration

You use data sources when:
- Infrastructure already exists
- You need to reference outputs from another system
- You want to dynamically look up values (IDs, IPs, ARNs, names)

Common use cases:
- Get an existing VPC ID
- Find the latest AMI
- Read secrets from a vault
- Look up DNS records
- Reference resources created outside Terraform
