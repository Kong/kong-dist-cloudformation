# [KONG][website-url] :heavy_plus_sign: [AWS CloudFormation](https://aws.amazon.com/cloudformation/)

[![Website][website-badge]][website-url]
[![Documentation][documentation-badge]][documentation-url]
[![Mailing List][mailing-list-badge]][mailing-list-url]
[![Gitter Badge][gitter-badge]][gitter-url]

[![][kong-logo]][website-url]

This CloudFormation template helps you model and set up Kong's resources in AWS easily.

Note: For Kong's version older than 0.5.x use the tag 2.0.2.

## Summary

You have option to chose between two templates:

###  1) Kong with Cassandra DB

Provision Kong resources along with a new [Cassandra cluster](http://cassandra.apache.org/), using The [Datastax Cassandra](http://docs.datastax.com/en/cassandra/2.2/cassandra/install/installAMI.html) AMI.

| Region            | HVM AMIs                                                               | PV AMIs                                                                |
| ----------------: | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `us-east-1`       | [![Kong Stack launch][stack-badge]][us-east-1-caas-hvm-stack-url]      | [![Kong Stack launch][stack-badge]][us-east-1-caas-pv-stack-url]       |
| `us-west-1`       | [![Kong Stack launch][stack-badge]][us-west-1-caas-hvm-stack-url]      | [![Kong Stack launch][stack-badge]][us-west-1-caas-pv-stack-url]       |
| `us-west-2`       | [![Kong Stack launch][stack-badge]][us-west-2-caas-hvm-stack-url]      | [![Kong Stack launch][stack-badge]][us-west-2-caas-pv-stack-url]       |
| `eu-west-1`       | [![Kong Stack launch][stack-badge]][eu-west-1-caas-hvm-stack-url]      | [![Kong Stack launch][stack-badge]][eu-west-1-caas-pv-stack-url]       |
| `ap-northeast-1`  | [![Kong Stack launch][stack-badge]][ap-northeast-1-caas-hvm-stack-url] | [![Kong Stack launch][stack-badge]][ap-northeast-1-caas-pv-stack-url]  |
| `ap-southeast-1`  | [![Kong Stack launch][stack-badge]][ap-southeast-1-caas-hvm-stack-url] | [![Kong Stack launch][stack-badge]][ap-southeast-1-caas-pv-stack-url]  |
| `ap-southeast-2`  | [![Kong Stack launch][stack-badge]][ap-southeast-2-caas-hvm-stack-url] | [![Kong Stack launch][stack-badge]][ap-southeast-2-caas-pv-stack-url]  |
| `sa-east-1`       | [![Kong Stack launch][stack-badge]][sa-east-1-caas-hvm-stack-url]      | [![Kong Stack launch][stack-badge]][sa-east-1-caas-pv-stack-url]       |

###  2) Kong without Cassandra DB (you need to bring yours)

Provisions Kong resources with user provided Cassandra seed nodes.

| Region            | HVM AMIs                                                           | PV AMIs                                                          |
| ----------------: | ------------------------------------------------------------------ | ---------------------------------------------------------------- |
| `us-east-1`       | [![Kong Stack launch][stack-badge]][us-east-1-hvm-stack-url]       | [![Kong Stack launch][stack-badge]][us-east-1-pv-stack-url]      |
| `us-west-1`       | [![Kong Stack launch][stack-badge]][us-west-1-hvm-stack-url]       | [![Kong Stack launch][stack-badge]][us-west-1-pv-stack-url]      |
| `us-west-2`       | [![Kong Stack launch][stack-badge]][us-west-2-hvm-stack-url]       | [![Kong Stack launch][stack-badge]][us-west-2-pv-stack-url]      |
| `eu-west-1`       | [![Kong Stack launch][stack-badge]][eu-west-1-hvm-stack-url]       | [![Kong Stack launch][stack-badge]][eu-west-1-pv-stack-url]      |
| `ap-northeast-1`  | [![Kong Stack launch][stack-badge]][ap-northeast-1-hvm-stack-url]  | [![Kong Stack launch][stack-badge]][ap-northeast-1-pv-stack-url] |
| `ap-southeast-1`  | [![Kong Stack launch][stack-badge]][ap-southeast-1-hvm-stack-url]  | [![Kong Stack launch][stack-badge]][ap-southeast-1-pv-stack-url] |
| `ap-southeast-2`  | [![Kong Stack launch][stack-badge]][ap-southeast-2-hvm-stack-url]  | [![Kong Stack launch][stack-badge]][ap-southeast-2-pv-stack-url] |
| `sa-east-1`       | [![Kong Stack launch][stack-badge]][sa-east-1-hvm-stack-url]       | [![Kong Stack launch][stack-badge]][sa-east-1-pv-stack-url]      |
 
 
### Parameters
 
| Parameter                   | Default      | Description                                                                          |
| --------------------------: | ------------ | ------------------------------------------------------------------------------------ |
| `SSHLocation`               | `0.0.0.0/0`  | The IP address range that can be used to SSH to the Kong and Cassandra EC2 instances |
| `KongProxyAccess`           | `0.0.0.0/0`  | The IP address range that can be used to access the Kong admin server                |
| `KongAdminAccess`           | `0.0.0.0/0`  | The IP address range that can be used to access the Kong proxy server                |
| `KongKeyName`               | `-`          | Existing EC2 KeyPair to enable SSH access to the Kong instances                      |
| `KongFleetMaxSize`          | `2`          | Max Number of Kong instances *(Min: `1`)*                                 |
| `KongFleetDesiredSize`      | `2`          | Desired Number of Kong instances *(Min: `1`)*                             |
| `KongInstanceType`          | `c3.8xlarge` | EC2 instance type for Kong. Note: T2 instance is not supported on the EC2-Classic platform |
| `KongVersion`               | `-`          | Kong version, leave empty to install latest version                                  |
| `KongAvailabilityZones`     | `-`          | AZ for the Kong instances                                                            |
| `CassandraKeyName`          | `-`          | Existing EC2 KeyPair to enable SSH access to the instances for Cassandra             |
| `CassandraFleetSize`        | `1`          | Number of nodes in cluster. *(Min: `1`)*                                  |
| `CassandraAvailabilityZone` | `-`          | Availablity zone in which cassandra cluster would be created, *for multi regions and zones cluster please refer to [Datastax documentation](http://docs.datastax.com/en/cassandra/2.2/cassandra/planning/planPlanningEC2.html?scroll=planPlanningEC2__multi-region-deploy).* |
| `CassandraInstanceType`     | `c3.2xlarge` | EC2 instance type for Cassandra                                                      |
| `CassandraClusterName`      | `-`          | Cassandra cluster name                                                               |
| `CassandraClusterVersion`   | `2.2.4`      | Cassandra cluster version                                                            |
| `CassandraVersion`          | `Community`  | Cassandra version                                                                    |
| `CassandraOpsCenterAccess`  | `0.0.0.0/0`  | The IP address range that can access OpsCenter for Cassandra cluster management      |


### Instructions:

1. **Key Pairs**:

    Create two sets of key pairs, one to access Cassandra instances & one for Kong instances. *Continue to next step if you want to use an existing key pair*

3. **Choose a Region & VM Type**:

    Choose the region closest to your API servers, and pick the virtualization type you'd like from the list of available [templates](#tempaltes) above.

    You should land on AWS Cloud Formation *"Select Template"* page

4. **Parameters**:

    Fill in all the parameters details. If you chose to launch Kong with Cassandra you would be asked to fill in extra parameters to create a Cassandra cluster. check the description of each field and provide appropriate values.

    **Note**: *consult the [parameters table](#parameters) for detailed description of parameters*

5. **Option page**:

    Add Tags and other fields according to your requirements.  

    **Note:** *The template is configured to add a "Name" tag to each relevant resource*

6. **Grab a Coffee!**:

    It will take several minutes *(~20 minutes)* to create the stack. Once the stack has a status of `CREATE_COMPLETE`, click on *"Output"* tab to get the proxy and Admin URL, it may take *60 seconds* more for links to become active.

    **Note**: *To monitor the progress go to AWS CloudFormation console, select the stack in the list. In the stack details pane, click the "Events" tab to see the progress.*
   
7. **Use Kong:**

    Quickly learn how to use Kong with the [5-minute Quickstart](http://localhost:3000/docs/0.4.x/getting-started/quickstart/).

#### SSL Support

You can install SSL Certificate on the Kong Load Balancer or use the SSl plugin on Kong to enable HTTPS support.

#####  1) [SSL Certificate for Kong Load Balancer](http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/ssl-server-cert.html)

1. Obtain the Kong Load Balancer `id` from the *"Resources tab"*.
2. Find the matching Kong Load Balancer instance.
6  Edit Listeners from the bottom pane, click Add.
7. In the Load Balancer Protocol column, select HTTPS (Secure HTTP). This updates the Load Balancer Port, Instance Protocol, and Instance Port columns. In the Instance Protocol column, select HTTP and update the Instance port to 8000.
8. By default, Elastic Load Balancing selects the current predefined security policy, ELBSecurityPolicy-2015-05, for your HTTPS/SSL listener. This is the recommended setting.
9. In the SSL Certificate column, click Change, and then you either upload a new certificate or choose an existing Certificate.
10. Click Save to add the listeners you just configured.
11. Click on Security tab. 
12. Click on Security Group id.
13. In the bottom pane, select the Inbound tab.
14. Click Edit.
15. Add Load Balancer Port for the HTTPS to the list and save.

#####  2) [Using Kong SSL Plugin](https://getkong.org/plugins/ssl/)

1. SSH on each Kong node, upload the Certificate.
2. Update Kong node Security Group to open TCP port 8443.
3. Add HTTPS listener on Kong Load Balancer forwarding request to 8443 Instance port.
4. Open HTTPS listener port in Kong Load Balancer security group.
5. Enable the Kong [SSL plugin](https://getkong.org/plugins/ssl/).
     
     
#### Important Note

1. The security configuration on the templates opens up all externally accessible ports to incoming traffic from any IP address if default is chosen *(`0.0.0.0/0`)*
2. The risk of data leakage is high. If you desire a more secure configuration, please update access fields with appropiate IP address range
3. The template installs many resources on AWS. You will be billed just for the AWS resources used
4. Some of the instance types may not be supported in all the AWS Regions or Availiblity Zones, so chose next best available option


## Enterprise Support

Support, Demo, Training, API Certifications and Consulting available at http://getkong.org/enterprise.

[kong-logo]: http://i.imgur.com/4jyQQAZ.png
[website-url]: https://getkong.org/
[website-badge]: https://img.shields.io/badge/GETKong.org-Learn%20More-43bf58.svg
[documentation-url]: https://getkong.org/docs/
[documentation-badge]: https://img.shields.io/badge/Documentation-Read%20Online-green.svg
[gitter-url]: https://gitter.im/Mashape/kong
[gitter-badge]: https://img.shields.io/badge/Gitter-Join%20Chat-blue.svg
[mailing-list-badge]: https://img.shields.io/badge/Email-Join%20Mailing%20List-blue.svg
[mailing-list-url]: https://groups.google.com/forum/#!forum/konglayer


[us-east-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[us-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[us-west-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[eu-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[ap-northeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[ap-southeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[ap-southeast-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[sa-east-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-hvm.template
[us-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[us-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[us-west-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[eu-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[ap-northeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[ap-southeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[ap-southeast-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[sa-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-cassandra-pv.template
[us-east-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[us-west-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[us-west-2-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[eu-west-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[ap-northeast-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[ap-southeast-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[ap-southeast-2-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[sa-east-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-hvm.template
[us-east-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[us-west-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[us-west-2-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[eu-west-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[ap-northeast-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[ap-southeast-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[ap-southeast-2-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[sa-east-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Flatest%2Fkong-elb-pv.template
[stack-badge]: https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png
