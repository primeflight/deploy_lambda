# deploy_lambda

GitHub action that deploys packaged code in a repo into an AWS lambda function every time we commit code to the main branch of the repo.

## Commands

git add *
git commit -m "deploy_lambda action"
git tag -a -m "deploy_lambda action V1" v1.0.0
git push --follow-tags


## Creating your first workflow

1. Create a .github/workflows directory in your repository on GitHub if this directory does not already exist.

2. In the .github/workflows directory, create a file named main.yml

```bash
on: [push]

jobs:
  lambda_deployment:
    runs-on: ubuntu-latest
    name: Deploy code in repo into a lambda function
    steps:
      - name: 🏷 Code checkout
        id: checkout
        uses: actions/checkout@master
      - name: 📦 Package code into zip
        id: Package
        run: zip -r package.zip lambda_function.py
      - name: 🚀 Deploy Lambda
        id: Deploy
        uses: primeflight/deploy_lambda@v1.0.0
        with:
          access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          access-key-secret: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          region: ${{ secrets.AWS_REGION }}
          lambda-name: ${{ secrets.LAMBDA_NAME }}
          zip-file: package.zip
```


## Reference

- [Deploying AWS Lambdas with Custom GitHub Actions](https://embeddedinn.xyz/articles/tutorial/deploying-aws-lambdas-with-github-actions/)