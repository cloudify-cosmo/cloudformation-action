Creates an AWS CloudFormation environment.

# Prerequisites

The Cloudify CloudFormation Integration blueprint must be uploaded to Cloudify Manager, with the ID
`cloudify-cloudformation-1.0`.

## Environment Variables

This Action uses the Cloudify Profile environment variables described in the official
Cloudify documentation (see [More Information](#more-information) below).

In addition, the following environment variables are used:

| Name | Description
| -----|------------
| `AWS_ACCESS_KEY_ID` | AWS access key ID to use for AWS access
| `AWS_SECRET_ACCESS_KEY` | AWS secret key to use for AWS access
| `AWS_REGION` | AWS region to use for the stack; if not specified, then the value of the `aws_region_name` Cloudify secret is used

# Inputs

(Certain commonly-used inputs are documented in our official website; see [More Information](#more-information) below)

| Name | Description
|------|------------
| `stack-name` | CloudFormation's stack name
| `template-file` | Path to the file containing the template
| `bucket-name` | Name of S3 bucket to get the template from; if specified, then `resource_name`"` must also be specified
| `resource-name` | Name of file, within the bucket specified by `bucket_name`, containing the template to be used
| `template-url` | URL of CloudFormation template
| `parameters-file` | YAML/JSON file containing template parameters
| `outputs-file` | Path to JSON file to receive the Cloudify environment's outputs and capabilities

# Notes

* The template must be specified by exactly one of the following ways:
  * `template-file`, pointing to a file on the pipeline's workspace
  * Combination of `bucket-name` and `resource-name`, denoting an S3 bucket name and the path to
    a file within that bucket, respectively. The resource within the bucket must be publicly available.
  * `template-url`, which must be a URL to a resource hosted on S3, and accessible by the credentials
     provided to the pipeline.

# More Information

Refer to [Cloudify CI/CD Integration](https://docs.cloudify.co/latest/working_with/integration/) for additional information about
Cloudify's integration with CI/CD tools.
