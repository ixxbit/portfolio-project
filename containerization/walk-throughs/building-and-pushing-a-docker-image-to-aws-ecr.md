# Building and Pushing a docker image to aws ECR



* [source page](https://dev.to/wingkwong/building-and-pushing-a-docker-image-to-amazon-ecr-with-github-actions-on0)

GitHub Actions enables you to create custom software development life cycle \(SDLC\) workflows directly in your GitHub repository.

Workflows are custom automated processes that you can set up in your repository to build, test, package, release, or deploy any project on GitHub. With workflows you can automate your software development life cycle with a wide range of tools and services.

In this post, you'll learn how to use a GitHub Actions workflow to build and push a new container image to Amazon ECR upon code change.

You must store workflows in the `.github/workflows` directory in the root of your repository. The files are in `.yml` or `.yaml` format.

Let's create one called `build.yml`.

The first part is the name of your workflow. It is used to display on your repository's actions page.  


```text
name: Building and pushing a docker image to Amazon ECR
```

The second part is `on`, which is the name of the GitHub event triggering the workflow.

You can provide a single event  


```text
on: push
```

or a list of events  


```text
on: [push, pull_request]
```

We can also add more configurations. For example, we can specify activity types. The below example shows it triggers the workflow on push or pull request only for the master branch and for the paths under `app/**`.  


```text
on:
  pull_request:
    paths:
    - app/**
    branches:         
    - master
  push:
    paths:
    - app/**
    branches:         
    - master          
```

The next part is `env`. We'll setup environment variables to provide configuration option and credentials via Github.  


```text
env:
  AWS_DEFAULT_REGION: ap-southeast-1
  AWS_DEFAULT_OUTPUT: json
  AWS_ACCOUNT_ID: ${{ secrets.AWS_ACCOUNT_ID }}
  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
  CONTAINER_IMAGE: example-container:${{ github.sha }}
```

Go to Github, navigate to Settings in your repository. Click Secrets.

Add three new secrets namely `AWS_ACCOUNT_ID`, `AWS_ACCESS_KEY_ID`, and `AWS_SECRET_ACCESS_KEY`.

[![image](https://res.cloudinary.com/practicaldev/image/fetch/s--peaB6EZA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094296-d7299900-55c4-11ea-92e7-00447d54826b.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--peaB6EZA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094296-d7299900-55c4-11ea-92e7-00447d54826b.png)

A workflow run is made up of one or more jobs. They run in parallel by default. Each job runs in an environment specified by `runs-on`.

A job contains a sequence of tasks called steps. Steps can run commands, run setup tasks, or run an action in your repository, a public repository, or an action published in a Docker registry.  


```text
jobs:
  build-and-push:
    name: Building and pushing image to AWS ECR
    runs-on: ubuntu-latest
    steps:

    - name: Checkout
      uses: actions/checkout@master

    - name: Setup ECR
      run: |
        $( aws ecr get-login --no-include-email )

    - name: Build and tag the image
      run: |
        docker build \
          -t $CONTAINER_IMAGE \
          -t $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE ./app

    - name: Push
      if: github.ref == 'refs/heads/master'
      run: |
        docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE
```

Let's break it out. There is a job called `build-and-push`. There are four steps running on a virtual environment which is Ubuntu 18.04.

The first step is to check out the master.  


```text
- name: Checkout
    uses: actions/checkout@master
```

Then, we need to setup our Amazon ECR in order to push our image to it.  


```text
    run: |
    $( aws ecr get-login --no-include-email )
```

The third step is to build and tag the docker image. Notice that we are using the environment variables defined in `env`.  


```text
- name: Build and tag the image
    run: |
    docker build \
        -t $CONTAINER_IMAGE \
        -t $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE ./app
```

The last step is to run `docker push` to push the image built in the previous step to Amazon ECR.  


```text
- name: Push
    if: github.ref == 'refs/heads/master'
    run: |
    docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE
```

Commit something under app directory and push the changes to master.

Navigate to Actions. You should see a workflow is being processed.

[![image](https://res.cloudinary.com/practicaldev/image/fetch/s--cerOi-2M--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094355-3c7d8a00-55c5-11ea-8360-03df6cbd73df.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--cerOi-2M--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094355-3c7d8a00-55c5-11ea-8360-03df6cbd73df.png)

You can see the status or check the log for each step.  
[![image](https://res.cloudinary.com/practicaldev/image/fetch/s--e9_np8J1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094400-9ed68a80-55c5-11ea-91bc-a4a0fa269e48.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--e9_np8J1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://user-images.githubusercontent.com/35857179/75094400-9ed68a80-55c5-11ea-91bc-a4a0fa269e48.png)

You can see the latest tag name when you expand `Build and tag the image`.  


```text
Successfully built a1ffb1e3955b
Successfully tagged example-container:545385325b99e079cb7ee69d3809efd90cbffba9
Successfully tagged ***.dkr.ecr.ap-southeast-1.amazonaws.com/example-container:545385325b99e079cb7ee69d3809efd90cbffba9
```

Go to AWS ECR Console, you should see the image there.

That's it. Here's the complete build yaml file.  


```text
name: Building and pushing a docker image to Amazon ECR

on:
  pull_request:
    paths:
    - app/**
    branches:         
    - master
  push:
    paths:
    - app/**
    branches:         
    - master   

env:
  AWS_DEFAULT_REGION: ap-southeast-1
  AWS_DEFAULT_OUTPUT: json
  AWS_ACCOUNT_ID: ${{ secrets.AWS_ACCOUNT_ID }}
  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
  CONTAINER_IMAGE: example-container:${{ github.sha }}

jobs:
  build-and-push:
    name: Building and pushing image to AWS ECR
    runs-on: ubuntu-latest
    steps:

    - name: Checkout
      uses: actions/checkout@master

    - name: Setup ECR
      run: |
        $( aws ecr get-login --no-include-email )

    - name: Build and tag the image
      run: |
        docker build \
          -t $CONTAINER_IMAGE \
          -t $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE ./app

    - name: Push
      if: github.ref == 'refs/heads/master'
      run: |
        docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$CONTAINER_IMAGE
```

F

Useful article - I've done the equivalent of this in lots of different CI/CD platforms \(Azure DevOps, BitBucket, GitLab, Circle CI...\) but haven't used GitHub actions yet. Perhaps building and pushing a container is the "Hello World" of CI/CD?

