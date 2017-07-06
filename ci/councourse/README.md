# The Fly CLI

Login
```
fly -t target_name login --concourse-url http://192.168.100.4:8080
fly -t target_name sync
```

Execute task
```
fly -t target_name execute --config some_task.yml
```

Set pipeline
```
fly -t target_name set-pipeline --config pipeline.yml --pipeline pipeline_name
```

Delete pipeline
```
fly destroy-pipeline -t target_name --pipeline pipeline_name
```

View builds
```
fly -t target_name builds
```

View job output
```
fly -t target_name watch --job pipeline/job_name
```

Trigger job
```
fly -t target_name trigger-job --job pipeline/job_name
```
