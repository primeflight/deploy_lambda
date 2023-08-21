# deploy_lambda

GitHub action that deploys packaged code in a repo into an AWS lambda function every time we commit code to the main branch of the repo.

## Commands

git add *
git commit -m "deploy_lambda action"
git tag -a -m "deploy_lambda action V1" v1.0.0
git push --follow-tags

## Reference

- [Deploying AWS Lambdas with Custom GitHub Actions](https://embeddedinn.xyz/articles/tutorial/deploying-aws-lambdas-with-github-actions/)