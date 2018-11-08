# Serverless Image Processing.

> Deploy with one command to AWS Lambda and S3 ⚡️

## Getting Started

#### Clone to your local machine:

```bash
$ git clone https://github.com/slorenzo/serverless-image-processing.git
$ cd serverless-image-processing
```

### Deployment

#### 1. Set environment variables

Add your secret keys and configuration variables on `secrets.env`.
```env
AWS_KEY=XXX
AWS_SECRET=YYY
STAGE=dev
REGION=us-east-1
BUCKET=your-bucket-here
```

#### 2. Deploy

```bash
$ docker-compose up --build
```

The command line will log out the service endpoints and all info.

### Usage

After the service has been deployed, you will receive a bucket endpoint.

Let's upload an image so we have something to work with.
```bash
$ aws s3 cp --acl public-read IMAGE_NAME.jpg s3://BUCKET
```

Example 1:
```
http://BUCKET.s3-website.REGION.amazonaws.com/?f=IMAGE_NAME.jpg
```

Or you can access the lambda function directly.

Example 2:
```
https://LAMBDA_ID.execute-api.REGION.amazonaws.com/dev/processing?f=IMAGE_NAME.jpg
```

Complete guide of the different options:

| Query string name | Type   | Required | Description |
| ------------------ | ------ | -------- | ----------- |
| `f`                | String | Yes      | The complete image name uploaded to your S3 bucket (eg. placeholder.jpg)
| `w`                | Number | No       | Width
| `h`                | Number | No       | Height
| `q`                | Number | No       | Quality (between 1-100)
| `t`                | String | No       | Convert to (default is webp) Available values are [webp, jpeg and png]

## Made with ❤ by

- Sebastian Lorenzo (Javascript developer)
- E-mail: [SebastianLorenzo@gmail.com](mailto:SebastianLorenzo@gmail.com)
- StackOverflow: [sebastian-lorenzo](http://stackoverflow.com/users/1741027/sebastian-lorenzo?tab=profile)

## License

MIT license. Copyright © 2018.