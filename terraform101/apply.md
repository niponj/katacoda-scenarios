Once the plan has been created we need to apply it to reach our desired state.
* Applies the plan, issuing API calls to providers in order to meet the desired state
* Creates or updating the statefile
* Output will indicate the changes and the resulting configuration
* Warning: apply will destroy and modify as well as create (plan will also tell you this)
* Terraform is eventually consistent and may partially succeed at matching the desired state. Subsequent apply commands will attempt to reconcile all resources to match the desired configuration on each run. 

Using the CLI, terraform will pull any images required and launch new containers.

`terraform apply`{{execute}}

Note that unless the -auto-approve CLI option is used, you must type "yes" to confirm before changes are applied.

`terraform apply -auto-approve`{{execute}}
