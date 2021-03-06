#### Security Groups

Security group templates are very similar to the [Firewalls on GCP](https://cloud.google
.com/compute/docs/networks-and-firewalls#firewalls). **They describe the allowed inbound traffic 
to the instances in the cluster.** Currently only one security group template can be selected for a Cloudbreak cluster 
and all the instances have a public IP address so all the instances in the cluster will belong to the same security 
group. This may change in a later release.

*Default Security Group*

You can also use the two pre-defined security groups in Cloudbreak.

`only-ssh-and-ssl:` all ports are locked down except for SSH and the selected Ambari Server HTTPS (you can't access Hadoop services 
outside of the virtual network):

* SSH (22)
* HTTPS (443)

*Custom Security Group*

You can define your own security group by adding all the ports, protocols and CIDR range you'd like to use. The rules
 defined here doesn't need to contain the internal rules, those are automatically added by Cloudbreak to the security
  group on GCP.

{!docs/common/ports.md!}

If `Public in account` is checked all the users belonging to your account will be able to use this security group 
template to create clusters, but cannot delete it.

>**NOTE:** The security groups are created on GCP only after the cluster provisioning starts with the selected 
security group template.

![](/images/ui-secgroup_v3.png)
<sub>*Full size [here](/images/ui-secgroup_v3.png).*</sub>
