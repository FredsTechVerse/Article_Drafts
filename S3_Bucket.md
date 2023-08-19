
#### A DEEPER DIVE INTO THE S3 BUCKET

- Bucket policies, ACLs, and IAM policies provide various ways to control access to S3 buckets and their objects
- The "Block Public Access" checkbox is a master switch that overrides these permissions and blocks all public access when enabled.
- When both a bucket policy and an IAM policy apply to a user, the more restrictive policy takes precedence.
- Error messages are quite sleek. We get to know the error by the first line then additional found in the $metadataObject... All in betweeen is whining about where the error could be .
- CORS (Cross origin resource sharing) - Simply involves two domains talking to each other and that is why we have the CORS policy you know and the CORS configuration in the index.js you know , incase another domain wants to access our resources eg the way the frontend is accessing resources in the backend which are on two different domains.

#### DEFINATIONS

**_ Policy _** - This is a JSON document that defines who has access and explicitly states to which resources they have access to and what actions they can perform on those resources.
**_Statement_**- This is a JSON block [Array so can contain multiple objects] that contains the permissions being granted / denied as well us conditions (optional) associated with the permissions.

- It is worth noting that a policy can contain multiple statements and each statement can contain multiple permissions which grant/deny access to one or more resources.

**_Bucket Policies_**: Used to control access to an S3 bucket. They are applied at the bucket level and define who (principal) can perform specific actions (such as GetObject, PutObject, DeleteObject) on the objects within the bucket.

- Bucket policies are useful when you want to grant or restrict access to your bucket to specific principals, including AWS accounts, IAM users, IAM roles, or even anonymous users. They are typically used for cross-account access or granting public access to specific resources.

- **_IAM Policies:_** Used to control access to AWS resources at a broader level. They are attached to IAM users, groups, or roles and define what actions those entities can perform on which resources.
- IAM policies are not specific to S3 buckets but apply to a wide range of AWS services. They are used to manage access within an AWS account and are more granular and flexible compared to bucket policies.
- IAM policies can be used to control access to multiple buckets or other AWS resources, not just S3 buckets.

**_Access Control List (ACL)_** is a legacy method for controlling access to individual objects within an S3 bucket. It predates bucket policies and is an older permission system for S3.
**_ CORS (Cross-Origin Resource Sharing) policies _**come into play when you want to control access to resources in an S3 bucket from a web page served from a different origin.

#### IS A CORS POLICY NECESSARY IN BUCKET PERMISSIONS ?

- Bucket policies control access to S3 resources at the bucket level, defining who can perform specific actions on the bucket and its objects. On the other hand, CORS policies control access to S3 resources from web browsers when making cross-origin requests.
- In the sample CORS policy you provided, the configuration allows requests from any origin (AllowedOrigins: ["*"]) to access the S3 resources using the specified methods (AllowedMethods: ["PUT", "HEAD", "GET", "POST"]). It also allows any headers (AllowedHeaders: ["*"]) and doesn't specify any headers to be exposed (ExposeHeaders: []).

- By configuring the CORS policy, you enable cross-origin requests from web browsers, which is necessary if you plan to serve resources from your S3 bucket on web pages hosted on different origins. The CORS policy works alongside the bucket policy to provide the necessary access control and security measures.

**_IAM AND BUCKET POLICY STRUCTURES_**

Let's summarize the different properties in the provided bucket and IAM policies and explain what they mean:

**_Bucket Policy_**

- Version: Specifies the version of the policy language being used. In this case, it is "2012-10-17," indicating the policy language version.
- Id: An optional identifier for the policy. It can be used for reference or management purposes.
- Statement: An array of policy statements. Each statement defines a set of permissions.
  - Sid: An optional identifier for the statement, used for reference or management purposes.
  - Effect: Specifies whether the permissions defined in the statement are allowed or denied. In this case, it is set to "Allow," indicating the specified actions are allowed.
  - Principal: Specifies the entity to which the policy applies. In this case, it is set to "\_" (asterisk), indicating any user or entity.
  - Action: Specifies the actions allowed or denied. In this case, "s3:GetObject," "s3:PutObject," and "s3:DeleteObject" actions are allowed.
  - Resource: Specifies the ARN (Amazon Resource Name) of the bucket or objects to which the policy applies. In this case, it is set to "arn:aws:s3:::aws-rocking-bucket/\_," indicating the policy applies to objects within the "aws-rocking-bucket" bucket.

**_IAM Policy_**

- Version: Specifies the version of the policy language being used. In this case, it is "2012-10-17," indicating the policy language version.
- Statement: An array of policy statements. Each statement defines a set of permissions.
- Sid: An optional identifier for the statement, used for reference or management purposes.
  - Effect: Specifies whether the permissions defined in the statement are allowed or denied. In this case, it is set to "Allow," indicating the specified actions are allowed.
  - Action: Specifies the actions allowed or denied. In this case, "s3:PutObject," "s3:GetObject," and "s3:DeleteObject" actions are allowed.
  - Resource: Specifies the ARNs of the resources to which the policy applies. In this case, it includes the ARNs for three buckets: "arn:aws:s3:::kapesha001-demo/," "arn:aws:s3:::aws-rocking-bucket/," and "arn:aws:s3:::freds-portfolio/\_."

**_IAM Policy_**

````json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::kapesha001-demo/*",
                "arn:aws:s3:::aws-rocking-bucket/*",
                "arn:aws:s3:::freds-portfolio/*"
            ]
        }
    ]
}

```
**_Bucket Policy_**

```json
{
  "Version": "2012-10-17",
  "Id": "Policy1675663952753",
  "Statement": [
    {
      "Sid": "Stmt1675663908702",
      "Effect": "Allow",
      "Principal": "_",
      "Action": ["s3:GetObject", "s3:PutObject", "s3:DeleteObject"],
      "Resource": "arn:aws:s3:::aws-rocking-bucket/_"
    }
  ]
}
```

#### SUMMARY

The bucket policy allows any user (represented by "\_") to perform "s3:GetObject," "s3:PutObject," and "s3:DeleteObject" actions on objects within the "aws-rocking-bucket" bucket. The IAM policy grants an IAM user or role permissions to perform the same actions on objects within the "kapesha001-demo," "aws-rocking-bucket," and "freds-portfolio" buckets. Both policies use the "Allow" effect, indicating that the specified actions are permitted.

