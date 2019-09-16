# No Task Pipeline

A pipeline without tasks, simply for testing the lowest-hanging UI.

## Create a project to work in

Create a new project (which is auto selected) so we can a new space to work in:

```
$ oc new-project tutorial-no-task-pipeline
```

*Note:* This project name is not used after this step, `oc` maintains the selection for the following steps; so feel free to change it.


## Create the Pipelines

Create the [no-task pipeline](no-task-pipeline.yaml) and the [no-task pipeline with resources](no-task-pipeline-with-resources.yaml) that exists in this folder.

```
$ oc create -f ./no-task-pipeline.yaml
$ oc create -f ./no-task-pipeline-with-resources.yaml 
```

View that it was created:

```
$ tkn pipeline ls
NAME                              AGE              LAST RUN   STARTED   DURATION   STATUS
no-task-pipeline                  12 seconds ago   ---        ---       ---        ---
no-task-pipeline-with-resources   4 seconds ago    ---        ---       ---        ---
```
