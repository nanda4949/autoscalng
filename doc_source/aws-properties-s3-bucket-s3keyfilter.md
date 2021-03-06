# AWS::S3::Bucket S3KeyFilter<a name="aws-properties-s3-bucket-s3keyfilter"></a>

A container for object key name prefix and suffix filtering rules\.

**Note**  
The same type of filter rule cannot be used more than once\. For example, you cannot specify two prefix rules\.

## Syntax<a name="aws-properties-s3-bucket-s3keyfilter-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-properties-s3-bucket-s3keyfilter-syntax.json"></a>

```
{
  "[Rules](#cfn-s3-bucket-s3keyfilter-rules)" : [ FilterRule, ... ]
}
```

### YAML<a name="aws-properties-s3-bucket-s3keyfilter-syntax.yaml"></a>

```
  [Rules](#cfn-s3-bucket-s3keyfilter-rules): 
    - FilterRule
```

## Properties<a name="aws-properties-s3-bucket-s3keyfilter-properties"></a>

`Rules`  <a name="cfn-s3-bucket-s3keyfilter-rules"></a>
A list of containers for the key\-value pair that defines the criteria for the filter rule\.  
*Required*: Yes  
*Type*: List of [FilterRule](aws-properties-s3-bucket-filterrule.md)  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)