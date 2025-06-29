# serverlessimageprocessing-workflow-aws-rekogniton-stepfunctions
This project implements a fully serverless image processing pipeline using AWS Step Functions, Rekognition, Lambda, and S3. It detects faces, creates thumbnails, indexes faces into a collection, and stores metadata in DynamoDB. Originally based on the AWS Serverless Workshop, this version is customized and built manually using the AWS Console.

📸 Workflow Overview
- User uploads a photo to the RiderPhotos S3 bucket.
- The image triggers a Step Function that:
- Detects face(s) using Rekognition.
- Checks for duplicate face(s) in a Rekognition Collection.
- If valid, creates a thumbnail and indexes the face.
- Saves metadata to a DynamoDB table.
- Notifies via SNS if image is invalid or duplicate.

🧱 Architecture
- Amazon S3: Stores rider images and thumbnails.
- AWS Lambda: Contains 5 Python-based functions:
- FaceDetectionFunction
- FaceSearchFunction
- IndexFaceFunction
- ThumbnailFunction (uses Pillow)
- CopyS3ObjectsFunction (for test images)
- Amazon Rekognition: Face detection and indexing.
- Amazon DynamoDB: Stores metadata for indexed faces.
- AWS Step Functions: Orchestrates the image workflow.
 Amazon SNS: Sends notifications for invalid images.
