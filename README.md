# rabbitmq-aws-upstart

This is just a hack we had at getting new rabbitmq-nodes to join existing clusters if behind a common load balancer.  The customisation does the following:

1. Call the AWS meta-data API from AWS to get the instance's instance-id.
1. Then (assuming you give the instance a sufficient instance role to query the AWS API), we describe the load balancer and get a list of instances excluding our own.
1. Call describe instances to get the local-dns address for one of the existing cluster members.
