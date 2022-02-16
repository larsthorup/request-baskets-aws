# request-baskets-aws

AWS infrastructure for self-hosted https://github.com/darklynx/request-baskets

- Set AWS credentials
- ECR_HOST

```bash
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin $ECR_HOST
docker build -t request-baskets .
docker tag request-baskets:latest $ECR_HOST/request-baskets:latest
docker push $ECR_HOST/request-baskets:latest
terraform init --backend-config="region=eu-west-1" --backend-config="bucket=test-terraform-state" --backend-config="key=request-baskets"
terraform graph
terraform apply
```
