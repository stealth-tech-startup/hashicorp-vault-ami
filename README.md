# HashiCorp Vault AMI Build Specification

This repository contains resources and configuration scripts for building a custom [HashiCorp Vault][HashiCorp Vault] 
[AMI][AWS AMI] with [HashiCorp Packer][HashiCorp Packer].

**Check out the AMI's [user guide](doc/USER_GUIDE.md) for more information.**

## 🚀 Getting started

If you are new to HashiCorp Vault, we recommend following the [Vault tutorials][HashiCorp Vault tutorials]. If you
already have an HCP account and you want to launch an HCP Vault cluster on your account, see
[Hashicorp Cloud Platform][Hashicorp Cloud Platform].

## 🔢 Pre-requisites

You must have [Packer][HashiCorp Packer] version 1.8.0 or later installed on your local system. For more information,
see [Installing Packer][Installing Packer] in the Packer documentation. You must also have AWS account credentials
configured so that Packer can make calls to AWS API operations on your behalf. For more information, see
[Authentication][Authentication] in the Packer documentation.

## 👷 Building the AMI

A [Makefile](./Makefile) is provided to build the Vault AMI, but it is just a small wrapper around invoking Packer
directly. We can initiate the build process by running the following command in the root of this repository:

```bash
make
```

By default, the Makefile chooses the most recent Vault binary to build the AMI

**Note**
The default instance type to build this AMI does not qualify for the AWS free tier. You are charged for any instances
created when building this AMI.

## ⚖️ License Summary

This sample code is made available under a modified MIT license. See the [LICENSE file](./LICENSE).


[Authentication]: https://www.packer.io/docs/builders/amazon.html#specifying-amazon-credentials
[AWS AMI]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html

[Hashicorp Cloud Platform]: https://cloud.hashicorp.com/
[HashiCorp Packer]: https://www.packer.io/
[HashiCorp Vault]: https://www.vaultproject.io/
[HashiCorp Vault tutorials]: https://developer.hashicorp.com/vault/tutorials

[Installing Packer]: https://www.packer.io/docs/install/index.html
