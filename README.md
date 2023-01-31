HashiCorp Vault AMI Build Specification
=======================================

This repository contains resources and configuration scripts for building a custom [HashiCorp Vault][HashiCorp Vault] 
[AMI][AWS AMI] with [HashiCorp Packer][HashiCorp Packer].

**Check out the AMI's [user guide](doc/USER_GUIDE.md) for more information.**

🚀 Getting started
------------------

If you are new to HashiCorp Vault, we recommend following the [Vault tutorials][HashiCorp Vault tutorials]. If you
already have an HCP account and you want to launch an HCP Vault cluster on your account, see
[Hashicorp Cloud Platform][Hashicorp Cloud Platform].

🔢 Pre-requisites
-----------------

To use build this AMI, the following will be needed:

- [Packer][HashiCorp Packer] version 1.8.0 or later installed. For more information, see
   [Installing Packer][Installing Packer] in the Packer documentation.
- An [AWS account][AWS portal]
- [Local environment variables for your AWS account][AWS local env variables setup].

Clone the repository.

```bash
git clone -b master https://github.com/stealth-tech-startup/hashicorp-vault-ami.git
```

Change into the cloned repo directory.

```bash
cd hashicorp-vault-ami
```

Create a Local SSH Key
----------------------

Create a local SSH key to pair with the new terraform user to be created on this instance.

```bash
ssh-keygen -t rsa -C "your_email@example.com" -f ./hashicorp-vault
```

The command above generates a new SSH key called `hashicorp-vault`. The argument provided with the `-f` flag creates the
key in the current directory and creates two files called `hashicorp-vault` and `hashicorp-vault.pub`. Change the 
placeholder email address accordingly if needed.

When prompted, press enter to leave the passphrase blank on this key.

👷 Building the AMI
--------------------

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
[AWS local env variables setup]: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html#envvars-set
[AWS AMI]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html
[AWS portal]: https://portal.aws.amazon.com/billing/signup?nc2=h_ct&src=default&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start

[Hashicorp Cloud Platform]: https://cloud.hashicorp.com/
[HashiCorp Packer]: https://www.packer.io/
[HashiCorp Vault]: https://www.vaultproject.io/
[HashiCorp Vault tutorials]: https://developer.hashicorp.com/vault/tutorials

[Installing Packer]: https://developer.hashicorp.com/packer/tutorials/docker-get-started/get-started-install-cli

[Local environment variables for your AWS account][AWS local env variables setup].