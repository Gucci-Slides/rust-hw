# AWS Lambda with Rust
## Overview
Use AWS SAM for Infrastructure as Code to deploy a Lambda written in Rust
## Notes
Created an S3 bucket to store the artifacts before running `sam deploy --guided `  \
Must declare what architecture is used (x84_64) during build stage
```
cargo lambda build --release --target x86_64-unknown-linux-gnu
```

CodeUri requires the file path to the binary for the Lambda, and the Handler is the location of the binary itself \
Local invoke with the following code:
```
aws lambda invoke \
  --cli-binary-format raw-in-base64-out \
  --function-name rust-hw-HelloWorldFunction-tMmdcxXMP58f \
  --payload '{"command": "Say Hi!"}' \
  output.json
```

###CloudWatch Logs
Duration: 1.43 ms    Billed Duration: 27 ms    Memory Size: 128 MB    Max Memory Used: 15 MB    Init Duration: 24.94 ms
Note the bill duration is higher since a Docker image is built

Referenced this repo
https://github.com/awslabs/aws-lambda-rust-runtime#2-deploying-the-binary-to-aws-lambda
