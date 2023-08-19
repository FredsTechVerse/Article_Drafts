### WORKING WITH THE AWS SDK

- Things have been harmnized and made simple where there is a common pattern to this operations :-

  1.  Generating a command with the following syntax body ` const command = new DeleteObjectCommand({   Bucket: process.env.AWS_BUCKET_NAME,Key: Key,});`

  - The command entails kinda like a callback function for performing our operation which is then passed to the specific bucket and the fileName (Key)
  - The commands include :-
    - GetObjectComand - Used for fetching a resource from the bucket
    - PutObjectCommand - Used for uploading a resource to the bucket
    - DeleteObjectCommand - Used for deleting a resource from the bucket
    - ListObjectsCommand - Used for listing all the resources in the bucket

  2.  We then invoke the method ` const response = await client.send(command);` and wallah we are done!What we do with our signed url is upto us!
  3.  Generating a presigned url is also simplified where we specify our command as normal ,then invoke the method `    const signedUrl = await getSignedUrl(client, command, { expiresIn: 300 });` and just like that we are done!

- Let us consume utilize jwt effectively by using the user data harnessed if possible instead of passing it manually.
