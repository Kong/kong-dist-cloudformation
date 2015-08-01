# KONG Cloudformation Stack Templates

- Website: [getkong.org][kong-url]
- Documentation: [getkong.org/docs][kong-docs]
- Mailing List: [Google Groups][google-groups-url]

[![][kong-logo]][kong-url]



Kong Cloudformation template helps you model and set up Kong resources in AWS easily.Tempalte describes all the resources need to start a Kong Proxy and Admin server behind a load balancer.


## Summary

You have option to choose between two templates, one provisions Kong resources along with a new Cassandra single node clusture another provisions kong resources with user provided Cassandra seed nodes. 

### Launching Kong with Cassandra



| Region          | Launch stack                                                                           |
| ---------------:|----------------------------------------------------------------------------------------|
| `us-east-1`          | HVM: [![Kong Stack launch][kong-stack-badge]][us-east-1-caas-hvm-stack-url]       |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][us-east-1-caas-pv-stack-url]         |
| `us-west-1`          | HVM: [![Kong Stack launch][kong-stack-badge]][us-west-1-caas-hvm-stack-url]       |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][us-west-1-caas-pv-stack-url]         |
| `us-west-2`          | HVM: [![Kong Stack launch][kong-stack-badge]][us-west-2-caas-hvm-stack-url]       |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][us-west-2-caas-pv-stack-url]         |
| `eu-west-1`          | HVM: [![Kong Stack launch][kong-stack-badge]][eu-west-1-caas-hvm-stack-url]       |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][eu-west-1-caas-pv-stack-url]         |
| `ap-northeast-1`     | HVM: [![Kong Stack launch][kong-stack-badge]][ap-northeast-1-caas-hvm-stack-url]  |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][ap-northeast-1-caas-pv-stack-url]    |
| `ap-southeast-1`     | HVM: [![Kong Stack launch][kong-stack-badge]][ap-southeast-1-caas-hvm-stack-url]  |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][ap-southeast-1-caas-pv-stack-url]    |
| `ap-southeast-2`     | HVM: [![Kong Stack launch][kong-stack-badge]][ap-southeast-2-caas-hvm-stack-url]  |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][ap-southeast-2-caas-pv-stack-url]    |
| `sa-east-1`          | HVM: [![Kong Stack launch][kong-stack-badge]][sa-east-1-caas-hvm-stack-url]       |
|				       | PV: [![Kong Stack launch][kong-stack-badge]][sa-east-1-caas-pv-stack-url]         |


### Bring your own Cassandra


| Region        | Launch stack                                                           |
| -------------:| -----------------------------------------------------------------------|
| `us-east-1`   | [![Kong Stack launch][kong-stack-badge]][kong-stack-url]               |

 
 
   







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


[us-east-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[us-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[us-west-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[eu-west-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[ap-northeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[ap-northeast-1-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template

[ap-southeast-2-caas-hvm-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-hvm-v1.0.template


[sa-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[us-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[us-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[us-west-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[eu-west-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[ap-northeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[ap-northeast-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template

[ap-southeast-2-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template


[sa-east-1-caas-pv-stack-url]: https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=kong-elb-cassandra&templateURL=https:%2F%2Fs3.amazonaws.com%2Fkong-cf-templates%2Fkong-elb-cassandra-pv-v1.0.template



[kong-stack-badge]: https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png


