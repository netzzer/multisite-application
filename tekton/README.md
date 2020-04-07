# Resources to deploy items with tekton
Ensure that the OpenShift pipeline operator is installed on the cluster before getting started

# Project
Create the project wordpress-tekton and create the following items

The git repository definition. Think of this as a variable file
```
oc create -f tekton-pipeline-resource.yaml 
```

The pipeline run is where multiple tasks are listed. This could be 1 task or many. This also tells the task which variables to use.
```
oc create -f tekton-pipeline.yaml
```

The task is something that you need a specific container to do. It can have multiple steps or just a single step. Think of it like a bash script. It will just run throw a list of things to do.
```
oc create -f tekton-task.yaml
```

# Deploying our app
We will still use kustomize to deploy our application. We already have configured kustomize to deploy in our tekton task. The only thing we need to do is to 
deploy the pipeline-run that relates to our environment. The example below will be for site1.

```
oc create -f tekton-pipeline-run-deploy-site1.yaml
```
