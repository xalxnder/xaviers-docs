# CI/CD

## **Continuous Integration**
[Continuous integration](https://aws.amazon.com/devops/continuous-integration/) is a software development practice where members of a team use a version control system and frequently integrate their work to the same location, such as a main branch. Each change is built and verified to detect integration errors as quickly as possible. Continuous integration is focused on automatically building and testing code, as compared to _continuous delivery_, which automates the entire software release process up to production.

## **Continuous Delivery** 
[Continuous delivery](https://aws.amazon.com/devops/continuous-delivery/) is a software development methodology where the release process is automated. Every software change is automatically built, tested, and deployed to production. Before the final push to production, a person, an automated test, or a business rule decides when the final push should occur. Although every successful software change can be immediately released to production with continuous delivery, not all changes need to be released right away.


### Gitlab

All of the fun takes place in the `.gitlab-ci.yml` file. 

```yml
#Self explamatory. Variables names to pass later
variables:
  IMAGE_NAME: xalxnder/demo-app
  IMAGE_TAG: python-app-1.0
 
#The names and order of the pipeline stages.
stages:
  - test
  - build
  - deploy

run_tests:
  stage: test
  #Use `image` to specify a Docker image that the job runs in. So this run_tests stage will run in the python:3.9-slim-buster image.
  image: python:3.9-slim-buster
  #Command/s to run before the script
  before_script:
    - apt-get update && apt-get install make
  #Shell script that is executed by a runner.
  script:
    - make test

build_image:
  stage: build
  image: docker:20.10.16
 # When you configure CI/CD, you specify an image, which is used to create the container where your jobs run. To specify this    image,   you use the `image` keyword. You can specify an additional image by using the `services` keyword. This additional image is used to create another container,     which is available to the first container. The two containers have access to one another and can communicate when running the job.
  services:
    - docker:20.10.16-dind
  variables:
    DOCKER_TLS_CERTDIR: "/certs"
  before_script:
  #For this example since we're using our own private docker registry, we'll need to login.
    - docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
  script:
  # Build docker Image
    - docker build -t $IMAGE_NAME:$IMAGE_TAG .
    #Push Image
    - docker push $IMAGE_NAME:$IMAGE_TAG

deploy:
  stage: deploy
  before_script:
    - chmod 400 $SSH_KEY
  script: ssh -o StrictHostKeyChecking=no -i $SSH_KEY root@216.155.152.132 "
      docker login docker.io -u $DOCKER_USERNAME -p $DOCKER_PASSWORD &&
      docker run -d -p 5000:5000 docker.io/$IMAGE_NAME:$IMAGE_TAG"
```


