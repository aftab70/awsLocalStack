# To deplpy the awsLocalStack container using docker composer 

nano docker-compose.yml

# Copy and paste the following config.

version: '3'
services:
  localstack:
    image: localstack/localstack
    ports:
      - "4563-4599:4563-4599"
      - "8055:8080"
    environment:
      - SERVICES=s3,lambda,cloudwatch,iam,apigateway
      - DEBUG=1
      - DATA_DIR=/tmp/localstack/data
      - LAMBDA_EXECUTOR=docker
    volumes:
      - "${TMPDIR:-/tmp/localstack}:/tmp/localstack"

# Deployment of AWS LocalStack

docker compose up -d

# Verify the LocalStack Container 

docker ps 

# Clean-up

docker-compose down

# 
      
