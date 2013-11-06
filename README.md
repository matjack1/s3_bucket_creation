s3_bucket_creation
==================

S3 bucket creation and setup for remote upload

1. Go to your AWS S3 Console: https://console.aws.amazon.com/s3/home 

2. Click "Create bucket"

  ![](https://raw.github.com/matjack1/s3_bucket_creation/master/1.png)

3. Open the properties of the new bucket

  ![](https://raw.github.com/matjack1/s3_bucket_creation/master/2.png)
  
  and click "Add CORS configurations"
  
  and add this code to allow the retrieval of the assets from every origin
  
  ```
  <CORSConfiguration>
      <CORSRule>
          <AllowedOrigin>*</AllowedOrigin>
          <AllowedMethod>GET</AllowedMethod>
          <MaxAgeSeconds>3000</MaxAgeSeconds>
          <AllowedHeader>Authorization</AllowedHeader>
      </CORSRule>
  </CORSConfiguration>
  ```
   
4. Go to your IAM console to edit users: https://console.aws.amazon.com/iam/home?#users
   
  Create a new user or pick an existing one and open the permissions tab

  ![](https://raw.github.com/matjack1/s3_bucket_creation/master/3.png)
     
  then add this policy
     
  ```
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Action": [
          "s3:*"
        ],
        "Sid": "Stmt1383677974000",
        "Resource": [
          "arn:aws:s3:::YOUR_BUCKET_NAME", "arn:aws:s3:::YOUR_BUCKET_NAME/*"
        ],
        "Effect": "Allow"
      },
      {
        "Action": [
          "s3:ListAllMyBuckets"
        ],
        "Sid": "Stmt1383678007000",
        "Resource": [
          "*"
        ],
        "Effect": "Allow"
      }
    ]
  }
  ```

It should work now, SO EASY.
