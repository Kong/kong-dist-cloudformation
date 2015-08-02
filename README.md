# KONG Cloudformation Templates

- Website: [getkong.org][kong-url]
- Documentation: [getkong.org/docs][kong-docs]
- Mailing List: [Google Groups][google-groups-url]

[![][kong-logo]][kong-url]



Kong Cloudformation template helps you model and set up Kong resources in AWS easily.Tempalte describes all the resources need to start a Kong Proxy and Admin server behind a load balancer.


## Summary

You have option to chose between two templates, one provisions Kong resources along with a new Cassandra single node clusture another provisions kong resources with user provided Cassandra seed nodes. 

In case if you chose Kong with Cassandra option, Template use [Datastax Cassandra](http://docs.datastax.com/en/cassandra/2.2/cassandra/install/installAMI.html) ami to create the Cassandra instance.The DataStax AMI allows you to set up a simple DataStax Community cluster using the Amazon Web Services EC2 Management Console. Installing via the AMI allows you to quickly deploy a Cassandra cluster within a single availability zone.


### Launching Kong with Cassandra



| Region          | virtualization Type                      | Launch stack                                 |
| ---------------:|------------------------------------------:|----------------------------------------------|
| `us-east-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][us-east-1-caas-hvm-stack-url]       |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][us-east-1-caas-pv-stack-url]         |
| `us-west-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][us-west-1-caas-hvm-stack-url]       |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][us-west-1-caas-pv-stack-url]         |
| `us-west-2`          | HVM |[![Kong Stack launch][kong-stack-badge]][us-west-2-caas-hvm-stack-url]       |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][us-west-2-caas-pv-stack-url]         |
| `eu-west-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][eu-west-1-caas-hvm-stack-url]       |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][eu-west-1-caas-pv-stack-url]         |
| `ap-northeast-1`     | HVM |[![Kong Stack launch][kong-stack-badge]][ap-northeast-1-caas-hvm-stack-url]  |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][ap-northeast-1-caas-pv-stack-url]    |
| `ap-southeast-1`     | HVM |[![Kong Stack launch][kong-stack-badge]][ap-southeast-1-caas-hvm-stack-url]  |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][ap-southeast-1-caas-pv-stack-url]    |
| `ap-southeast-2`     | HVM |[![Kong Stack launch][kong-stack-badge]][ap-southeast-2-caas-hvm-stack-url]  |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][ap-southeast-2-caas-pv-stack-url]    |
| `sa-east-1`          | HVM| [![Kong Stack launch][kong-stack-badge]][sa-east-1-caas-hvm-stack-url]       |
|				       | PV | [![Kong Stack launch][kong-stack-badge]][sa-east-1-caas-pv-stack-url]         |

### Launching kong with own Cassandra


| Region          | virtualization Type                      | Launch stack                                 |
| ---------------:|------------------------------------------:|----------------------------------------------|
| `us-east-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][us-east-1-hvm-stack-url]       |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][us-east-1-pv-stack-url]         |
| `us-west-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][us-west-1-hvm-stack-url]       |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][us-west-1-pv-stack-url]         |
| `us-west-2`          | HVM | [![Kong Stack launch][kong-stack-badge]][us-west-2-hvm-stack-url]       |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][us-west-2-pv-stack-url]         |
| `eu-west-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][eu-west-1-hvm-stack-url]       |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][eu-west-1-pv-stack-url]         |
| `ap-northeast-1`     | HVM | [![Kong Stack launch][kong-stack-badge]][ap-northeast-1-hvm-stack-url]  |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][ap-northeast-1-pv-stack-url]    |
| `ap-southeast-1`     | HVM | [![Kong Stack launch][kong-stack-badge]][ap-southeast-1-hvm-stack-url]  |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][ap-southeast-1-pv-stack-url]    |
| `ap-southeast-2`     | HVM | [![Kong Stack launch][kong-stack-badge]][ap-southeast-2-hvm-stack-url]  |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][ap-southeast-2-pv-stack-url]    |
| `sa-east-1`          | HVM | [![Kong Stack launch][kong-stack-badge]][sa-east-1-hvm-stack-url]       |
				       | PV |  [![Kong Stack launch][kong-stack-badge]][sa-east-1-pv-stack-url]         |
 
 
### Cloudformation parameters
 
| Parameter          | Description                                                           |
| ---------------:|---------------------------------------------------------------------------|   
|CassandraKeyName | Existing EC2 KeyPair to enable SSH access to the instances for Cassandra |
|CassandraVirtualisationType | Ec2 instance CassandraVirtualisationType for Cassandra        |
|CassandraSecurityGroupName | Existing SecurityGroup for Cassandra|
|CassandraAvailabilityZone| Availablity zone in which cassandra would be created|
|CassandraInstanceType|EC2 instance type for kong|
|CassandraClusterName|Cassandra cluster name|
|CassandraClusterVersion|Cassandra cluster version|
|CassandraVersion|Cassandra version|
|KongSSHLocation|Existing EC2 KeyPair to enable SSH access to the kong instance|
|KongProxyCidrIp|The IP address range that can be used to access the Kong admin server|
|KongAdminCidrIp|The IP address range that can be used to access the Kong proxy server|
|KongKeyName|Existing EC2 KeyPair to enable SSH access to the instances for Kong|
|KongFleetMaxSize|Max Number of Kong instances|
|KongFleetDesiredSize|Desired Number of Kong instances|
|KongInstanceType|EC2 instance type for kong|


### Steps to launch a kong stack on AWS cloud

1.	Please follow the [Datastax documention](http://docs.datastax.com/en/cassandra/2.2/cassandra/install/installAMISecurityGroup.html) to create a security group to open ports needed for funtioning of Cassandra clusture.(Jump to step 3 if you created your own Cassandra clusture)

2.	Create a key pair to access Cassandra instance.

3.	Create a key pair to access Kong instances.

4.	Select the region where you want kong stack to located and click launch stack. You should see AWS cloudformation "Select Tempalte" page.
		![Select Tempalte](../images/select_template.png)

5.	You can change the stack name. Click next to move to "Specify parameter" page.

6.	Fill in all the parameters details. If you chose to launch kong with cassandra you would be asked extra parameters to create a single  	  	node Cassandra clusture. Read description of field and enter the value for each field. 

7.	Click next to move to "Option page". Add Tags and other fields according to your requirements otherwise click next.

8.	Review the information for the stack. When you're satisfied with the settings, click Create

9.	AWS CloudFormation begins creating the resources that are specified in the template. To monitor the progress go to AWS CloudFormation    	console, select the stack MyWPTestStack in the list. In the stack details pane, click the Events tab. 

10. It will take several minutes(~ 15 minutes) to create the stack. Once the stack has a status of CREATE_COMPLETE, click on output tab 
	to get the proxy and Admin url.  
	 
	 	  
 











## Enterprise Support

Support, Demo, Training, API Certifications and Consulting available at http://getkong.org/enterprise.

[kong-url]: http://getkong.org/
[kong-docs]: http://getkong.org/docs/

[kong-logo]: http://i.imgur.com/4jyQQAZ.png
[kong-benefits]: http://cl.ly/image/1B3J3b3h1H1c/Image%202015-07-07%20at%206.57.25%20PM.png

[mashape-url]: https://www.mashape.com

[license-url]: https://github.com/Mashape/kong/blob/master/LICENSE
[license-badge]: https://img.shields.io/github/license/mashape/kong.svg

[gitter-url]: https://gitter.im/Mashape/kong
[gitter-badge]: https://img.shields.io/badge/Gitter-Join%20Chat-blue.svg

[google-groups-url]: https://groups.google.com/forum/#!forum/konglayer


[us-east-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[us-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[us-west-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[eu-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[ap-northeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[ap-southeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[ap-southeast-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template


[sa-east-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-hvm.template

[us-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[us-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[us-west-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[eu-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[ap-northeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[ap-southeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template

[ap-southeast-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template


[sa-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-cassandra-pv.template




[us-east-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[us-west-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[us-west-2-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[eu-west-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[ap-northeast-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[ap-southeast-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[ap-southeast-2-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-hvm&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template


[sa-east-1-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-hvm.template

[us-east-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[us-west-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[us-west-2-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[eu-west-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[ap-northeast-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[ap-southeast-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template

[ap-southeast-2-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template


[sa-east-1-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-pv&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fv1.0%2Fkong-elb-pv.template



[kong-stack-badge]: https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png


