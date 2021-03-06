# AWS::EC2::VPCEndpoint<a name="aws-resource-ec2-vpcendpoint"></a>

Specifies a VPC endpoint for a service\. An endpoint enables you to create a private connection between your VPC and the service\. The service may be provided by AWS, an AWS Marketplace Partner, or another AWS account\. For more information, see [VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html) in the *AWS PrivateLink User Guide*\.

A `gateway` endpoint serves as a target for a route in your route table for traffic destined for the AWS service\. You can specify an endpoint policy to attach to the endpoint, which controls access to the service from your VPC\. You can also specify the VPC route tables that use the endpoint\.

For information about connectivity when you use a gateway endpoint to connect to an Amazon S3 bucket from an EC2 instance, see [Why can’t I connect to an S3 bucket using a gateway VPC endpoint](http://aws.amazon.com/premiumsupport/knowledge-center/connect-s3-vpc-endpoint)\.

An `interface` endpoint is a network interface in your subnet that serves as an endpoint for communicating with the specified service\. You can specify the subnets in which to create an endpoint, and the security groups to associate with the endpoint network interface\.

A `GatewayLoadBalancer` endpoint is a network interface in your subnet that serves an endpoint for communicating with a Gateway Load Balancer that you've configured as a VPC endpoint service\.

## Syntax<a name="aws-resource-ec2-vpcendpoint-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-resource-ec2-vpcendpoint-syntax.json"></a>

```
{
  "Type" : "AWS::EC2::VPCEndpoint",
  "Properties" : {
      "[PolicyDocument](#cfn-ec2-vpcendpoint-policydocument)" : Json,
      "[PrivateDnsEnabled](#cfn-ec2-vpcendpoint-privatednsenabled)" : Boolean,
      "[RouteTableIds](#cfn-ec2-vpcendpoint-routetableids)" : [ String, ... ],
      "[SecurityGroupIds](#cfn-ec2-vpcendpoint-securitygroupids)" : [ String, ... ],
      "[ServiceName](#cfn-ec2-vpcendpoint-servicename)" : String,
      "[SubnetIds](#cfn-ec2-vpcendpoint-subnetids)" : [ String, ... ],
      "[VpcEndpointType](#cfn-ec2-vpcendpoint-vpcendpointtype)" : String,
      "[VpcId](#cfn-ec2-vpcendpoint-vpcid)" : String
    }
}
```

### YAML<a name="aws-resource-ec2-vpcendpoint-syntax.yaml"></a>

```
Type: AWS::EC2::VPCEndpoint
Properties: 
  [PolicyDocument](#cfn-ec2-vpcendpoint-policydocument): Json
  [PrivateDnsEnabled](#cfn-ec2-vpcendpoint-privatednsenabled): Boolean
  [RouteTableIds](#cfn-ec2-vpcendpoint-routetableids): 
    - String
  [SecurityGroupIds](#cfn-ec2-vpcendpoint-securitygroupids): 
    - String
  [ServiceName](#cfn-ec2-vpcendpoint-servicename): String
  [SubnetIds](#cfn-ec2-vpcendpoint-subnetids): 
    - String
  [VpcEndpointType](#cfn-ec2-vpcendpoint-vpcendpointtype): String
  [VpcId](#cfn-ec2-vpcendpoint-vpcid): String
```

## Properties<a name="aws-resource-ec2-vpcendpoint-properties"></a>

`PolicyDocument`  <a name="cfn-ec2-vpcendpoint-policydocument"></a>
\(Interface and gateway endpoints\) A policy to attach to the endpoint that controls access to the service\. If this parameter is not specified, we attach a default policy that allows full access to the service\.  
For CloudFormation templates in YAML, you can provide the policy in JSON or YAML format\. AWS CloudFormation converts YAML policies to JSON format before calling the API to create or modify the VPC endpoint\.  
*Required*: No  
*Type*: Json  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`PrivateDnsEnabled`  <a name="cfn-ec2-vpcendpoint-privatednsenabled"></a>
\(Interface endpoint\) Indicate whether to associate a private hosted zone with the specified VPC\. The private hosted zone contains a record set for the default public DNS name for the service for the Region \(for example, `kinesis.us-east-1.amazonaws.com`\) which resolves to the private IP addresses of the endpoint network interfaces in the VPC\. This enables you to make requests to the default public DNS name for the service instead of the public DNS names that are automatically generated by the VPC endpoint service\.  
To use a private hosted zone, you must set the following VPC attributes to `true`: `enableDnsHostnames` and `enableDnsSupport`\.  
Default: `false`  
*Required*: No  
*Type*: Boolean  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`RouteTableIds`  <a name="cfn-ec2-vpcendpoint-routetableids"></a>
\(Gateway endpoint\) One or more route table IDs\.  
*Required*: No  
*Type*: List of String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`SecurityGroupIds`  <a name="cfn-ec2-vpcendpoint-securitygroupids"></a>
\(Interface endpoint\) The ID of one or more security groups to associate with the endpoint network interface\.  
*Required*: No  
*Type*: List of String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`ServiceName`  <a name="cfn-ec2-vpcendpoint-servicename"></a>
The service name\. To get a list of available services, use the [DescribeVpcEndpointServices](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeVpcEndpointServices.html) request, or get the name from the service provider\.  
*Required*: Yes  
*Type*: String  
*Update requires*: [Replacement](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-replacement)

`SubnetIds`  <a name="cfn-ec2-vpcendpoint-subnetids"></a>
\(Interface and Gateway Load Balancer endpoints\) The ID of one or more subnets in which to create an endpoint network interface\. For a Gateway Load Balancer endpoint, you can specify one subnet only\.  
*Required*: Conditional  
*Type*: List of String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`VpcEndpointType`  <a name="cfn-ec2-vpcendpoint-vpcendpointtype"></a>
The type of endpoint\.  
Default: Gateway  
*Required*: No  
*Type*: String  
*Allowed values*: `Gateway | GatewayLoadBalancer | Interface`  
*Update requires*: [Replacement](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-replacement)

`VpcId`  <a name="cfn-ec2-vpcendpoint-vpcid"></a>
The ID of the VPC in which the endpoint will be used\.  
*Required*: Yes  
*Type*: String  
*Update requires*: [Replacement](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-replacement)

## Return values<a name="aws-resource-ec2-vpcendpoint-return-values"></a>

### Ref<a name="aws-resource-ec2-vpcendpoint-return-values-ref"></a>

When you pass the logical ID of this resource to the intrinsic `Ref` function, `Ref` returns the ID of the VPC endpoint\.

For more information about using the `Ref` function, see [Ref](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html)\.

### Fn::GetAtt<a name="aws-resource-ec2-vpcendpoint-return-values-fn--getatt"></a>

The `Fn::GetAtt` intrinsic function returns a value for a specified attribute of this type\. The following are the available attributes and sample return values\.

For more information about using the `Fn::GetAtt` intrinsic function, see [Fn::GetAtt](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html)\.

#### <a name="aws-resource-ec2-vpcendpoint-return-values-fn--getatt-fn--getatt"></a>

`CreationTimestamp`  <a name="CreationTimestamp-fn::getatt"></a>
The date and time the VPC endpoint was created\. For example: `Fri Sep 28 23:34:36 UTC 2018.`

`DnsEntries`  <a name="DnsEntries-fn::getatt"></a>
\(Interface endpoint\) The DNS entries for the endpoint\. Each entry is a combination of the hosted zone ID and the DNS name\. The entries are ordered as follows: regional public DNS, zonal public DNS, private DNS, and wildcard DNS\. This order is not enforced for AWS Marketplace services\.  
The following is an example\. In the first entry, the hosted zone ID is Z1HUB23UULQXV and the DNS name is vpce\-01abc23456de78f9g\-12abccd3\.ec2\.us\-east\-1\.vpce\.amazonaws\.com\.  
\["Z1HUB23UULQXV:vpce\-01abc23456de78f9g\-12abccd3\.ec2\.us\-east\-1\.vpce\.amazonaws\.com", "Z1HUB23UULQXV:vpce\-01abc23456de78f9g\-12abccd3\-us\-east\-1a\.ec2\.us\-east\-1\.vpce\.amazonaws\.com", "Z1C12344VYDITB0:ec2\.us\-east\-1\.amazonaws\.com"\]  
If you update the `PrivateDnsEnabled` or `SubnetIds` properties, the DNS entries in the list will change\.

`Id`  <a name="Id-fn::getatt"></a>
Not currently supported by AWS CloudFormation\.

`NetworkInterfaceIds`  <a name="NetworkInterfaceIds-fn::getatt"></a>
\(Interface endpoint\) One or more network interface IDs\. If you update the `PrivateDnsEnabled` or `SubnetIds` properties, the items in this list might change\.

## Examples<a name="aws-resource-ec2-vpcendpoint--examples"></a>



### VPC endpoint<a name="aws-resource-ec2-vpcendpoint--examples--VPC_endpoint"></a>

The following example specifies a VPC endpoint that allows only the s3:GetObject action on the examplebucket bucket\. Traffic to S3 within subnets that are associated with the routetableA and routetableB route tables is automatically routed through the VPC endpoint\. 

#### JSON<a name="aws-resource-ec2-vpcendpoint--examples--VPC_endpoint--json"></a>

```
{
   "S3Endpoint": {
      "Type": "AWS::EC2::VPCEndpoint",
	  "Properties": {
         "PolicyDocument": {
            "Version": "2012-10-17",
            "Statement": [{
               "Effect": "Allow",
               "Principal": "*",
               "Action": ["s3:GetObject"],
               "Resource": ["arn:aws:s3:::examplebucket/*"]
            }]
         },
         "RouteTableIds": [{"Ref": "routetableA"}, {"Ref": "routetableB"}],
         "ServiceName": {"Fn::Sub": "com.amazonaws.${AWS::Region}.s3"},
         "VpcId": {"Ref": "VPCID"}
      }
   }
}
```

#### YAML<a name="aws-resource-ec2-vpcendpoint--examples--VPC_endpoint--yaml"></a>

```
S3Endpoint:
  Type: 'AWS::EC2::VPCEndpoint'
  Properties:
    PolicyDocument:
      Version: 2012-10-17
      Statement:
        - Effect: Allow
          Principal: '*'
          Action:
            - 's3:GetObject'
          Resource:
            - 'arn:aws:s3:::examplebucket/*'
    RouteTableIds:
      - !Ref routetableA
      - !Ref routetableB
    ServiceName: !Sub 'com.amazonaws.${AWS::Region}.s3'
    VpcId: !Ref VPCID
```