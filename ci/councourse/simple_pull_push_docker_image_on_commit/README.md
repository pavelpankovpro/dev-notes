# Sample pull-push to docker hub pipeline

This pipeline does the following:

1) Defines git repo as resource to pull the code
```yml
resources:
- name: project-git
  type: git
  source:
    uri: path/to/git/repo
    branch: master
    private_key: ((project-git-key))
```

2) Defines a docker hub repo to pull from our containerized application image (and also to push the newly built image to the same repo on new commit)
```yml
- name: project-docker-image
  type: docker-image
  source:
    repository: dockerhub/repo
    username: ((docker-hub-username))
    password: ((docker-hub-password))
```

3) Defines a job with name `build-docker-image`
```yml
jobs:
- name: build-docker-image
  plan:
  - get: project-git
    trigger: true
  - put: project-docker-image
    params: {build: project-git/path/to/dockerfile/dir}
```

It will trigger on push in our specified branch in point 1)
```yml
- get: project-git
    trigger: true
```

Finally it will build the container image that is specified here:
```yml
params: {build: project-git/path/to/dockerfile/dir}
```

and will upload our image using our `project-docker-image` resource to docker hub
```yml
- put: project-docker-image
```

The `credentials.yml` file is used to store the docker hub username and password and ssh private key or any other information that you need to be separated from the main pipeline configuration file.

To set the pipeline using the configuration file use:
```bash
fly -t target_name set-pipeline --config pipeline.yml --pipeline pipeline_name --load-vars-from credentials.yml
```

