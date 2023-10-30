# Laravel-app-flyio

- https://portfolio-aik.fly.dev/

### Deploy fly.io

```bash
$ fly auth login

$ flyctl launch

$ fly auth token

### then you register this token 
### to your repository's secret actions

# make .github/workflows/main.yml
name: Fly Deploy
on: [push]
env:
  FLY_API_TOKEN: ${{ secrets.FLY_API_TOKEN }}
jobs:
  deploy:
      name: Deploy app
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v4 ### nowdays it enforced to use node 16, not node 12 version
                            ### so, actions/checkout@v4 is right, not actions/checkout@v2
        - uses: superfly/flyctl-actions/setup-flyctl@master
        - run: flyctl deploy

$ git add .
$ git commit -m "Configure auto-deploy through GitHub Actions"
$ git push

```

### REF

- https://fly.io/docs/laravel/advanced-guides/github-actions/#github-ci-action-auto-deploy-to-fly-io
