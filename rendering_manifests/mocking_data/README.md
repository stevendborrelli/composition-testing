# Mocking Cluster Data

This example shows various ways of Mocking data for the Composition. For example,
Provisioned Managed Resources or Environment Configs.

Directories:

- `context`: a JSON file of Context data availble to the Function
- `extra-resources`: Includes Extra Resources available to the function
- `observed`: Mock Existing Cluster Resources to use for `status`

To render run the following:

```shell
crossplane beta render \
  --extra-resources extra-resources \
  --observed-resources observed \
  --context-files="apiextensions.crossplane.io/environment"=environment/dev.json \
  --include-full-xr \
  --include-context \
  xr.yaml composition.yaml functions.yaml 
```

To validate the manifests, run:

```shell
crossplane beta render \
  --extra-resources extra-resources \
  --observed-resources observed \
  --context-files="apiextensions.crossplane.io/environment"=environment/dev.json \
  --include-full-xr \
  xr.yaml composition.yaml functions.yaml | crossplane beta validate . -
```
