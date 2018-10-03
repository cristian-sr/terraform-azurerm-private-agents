[![Build Status](https://jenkins-terraform.mesosphere.com/service/dcos-terraform-jenkins/job/dcos-terraform/job/terraform-azurerm-private-agents/job/master/badge/icon)](https://jenkins-terraform.mesosphere.com/service/dcos-terraform-jenkins/job/dcos-terraform/job/terraform-azurerm-private-agents/job/master/)

# Azure DC/OS Private Agent Instances

This module creates typical private agent instances

## EXAMPLE

```hcl
module "dcos-private-agent-instances" {
  source  = "dcos-terraform/private-agents/azure"
  version = "~> 0.1"

  subnet_id = "myid"
  security_group_ids = ["sg-12345678"]"
  public_ssh_key = "~/.ssh/id_rsa.pub"

  num_private_agents = "2"
  ...
}
```


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| admin_username | admin username | string | - | yes |
| allow_stopping_for_update | If true, allows Terraform to stop the instance to update its properties | string | `true` | no |
| dcos_instance_os | Operating system to use. Instead of using your own AMI you could use a provided OS. | string | - | yes |
| dcos_version | Specifies which DC/OS version instruction to use. Options: 1.9.0, 1.8.8, etc. See dcos_download_path or dcos_version tree for a full list. | string | - | yes |
| disk_size | disk size | string | - | yes |
| disk_type | Disk Type to Leverage. | string | `Standard_LRS` | no |
| hostname_format | Format the hostname inputs are index+1, region, cluster_name | string | `pvtagt-%[1]d-%[2]s` | no |
| image | image | string | - | yes |
| instance_type | instance type | string | - | yes |
| location | location | string | - | yes |
| name_prefix | Cluster Name | string | - | yes |
| num_private_agents | Specify the amount of private agents. These agents will provide your main resources | string | - | yes |
| public_ssh_key | public ssh key | string | - | yes |
| resource_group_name | resource group name | string | - | yes |
| ssh_private_key_filename | Path to the SSH private key | string | `/dev/null` | no |
| subnet_id | Subnet ID | string | - | yes |
| tags | Add custom tags to all resources | map | `<map>` | no |
| user_data | User data to be used on these instances (cloud-init) | string | `` | no |

## Outputs

| Name | Description |
|------|-------------|
| admin_username | SSH User |
| dcos_instance_os | Tested OSes to install with prereq |
| dcos_version | DCOS Version for prereq install |
| disk_size | Disk Size in GB |
| disk_type | Disk Type to Leverage |
| image | Source image to boot from |
| instance_type | Instance Type |
| name_prefix | Cluster Name |
| num_private_agents | Number of Instance |
| prereq_id | Returns the ID of the prereq script |
| private_ips | Private IP Addresses |
| public_ips | Public IP Addresses |
| public_ssh_key | SSH Public Key |
| resource_group_name | Resource Group Name |
| user_data | Customer Provided Userdata |

