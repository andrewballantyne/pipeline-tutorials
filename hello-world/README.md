# Hello World Example

A single pipeline, single task example to echo out hello world.

## Create a project to work in

Create a new project (which is auto selected) so we can a new space to work in:

```
$ oc new-project tutorial-hello-world
```

*Note:* This project name is not used after this step, `oc` maintains the selection for the following steps; so feel free to change it.


## Create the Task

Create the [hello-world task](task.yaml) that exists in this folder.

```
$ oc create -f ./task.yaml
```

View that it was created:

```
$ tkn task ls
NAME          AGE
hello-world   7 seconds ago
```


## Create the Pipeline

Create the [hello-world pipeline](pipeline.yaml) that exists in this folder.

```
$ oc create -f ./pipeline.yaml 
```

View that it was created:

```
$ tkn pipeline ls
NAME                   AGE              LAST RUN   STARTED   DURATION   STATUS
hello-world-pipeline   22 seconds ago   ---        ---       ---        ---
```

## Start the Pipeline (by creating the pipeline-run)

Create the [hello-world pipeline run](pipeline-run.yaml) that exists in this folder.

```
$ oc create -f pipeline-run.yaml
pipelinerun.tekton.dev/hello-world-pipeline created
```

View that it was created and it is running:

```
$ tkn pipelinerun ls
NAME                   STARTED         DURATION   STATUS
hello-world-pipeline   2 seconds ago   ---        Running
```

After a few seconds, viewing again shows it's finished:

```
$ tkn pipelinerun ls
NAME                   STARTED          DURATION     STATUS
hello-world-pipeline   28 seconds ago   27 seconds   Succeeded
```

Check the logs to see that it echoed out "hello world":

```
$ tkn pipeline logs
? Select pipeline : hello-world-pipeline
? Select pipelinerun : hello-world-pipeline started 4 minutes ago
[hello-world : build-step-echo] hello world

[hello-world : nop] Build successful
```
