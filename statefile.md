Terraform stores the state of the infrastructure and configuration it has deployed in terraform.tfstate JSON file:

Use the editor tree to the right to view the local terraform.tfstate file.

* The tfstate file can stored a file on disk (local) or remote storage (remote backend)
* 1--1 relationship of project to state
* Terraform interrogates the state file to establish diff of current vs desired 
* JSON format, simple to read / validate in tests
* Local state storage is default but only good for single user prototyping
* Use a [Remote state backend](https://www.terraform.io/docs/state/remote.html): 
(artifactory, azurerm, consul, etcd, etcdv3, gcs, http, manta, oss, pg, s3, swift, terraform enterprise)
* Remote state backend which are lock-aware and support state versioning are recommended 
* Protect state files - loss of a state != good

The terraform 'state' command supports subcommands for advanced state management. These subcommands can be used to slice and dice the Terraform state, and are specifically tailored to work with common Unix utilities such as grep, awk, etc. 

* list    List resources in the state
* mv      Move an item in the state
* pull    Pull current state and output to stdout
* push    Update remote state from a local state file
* rm      Remove instances from the state
* show    Show a resource in the state

`terraform state list`{{execute}}
<pre>
docker_container.nginx-server[0]
docker_image.nginx
</pre>

`terraform state show docker_container.nginx-server[0] | grep network_name`{{execute}}
<pre>
            network_name     = "bridge"
</pre>


The taint command can be used to manually mark a resource as tainted, forcing a destroy and recreate on the next plan/apply.
This will not modify your infrastructure immediately, the immediate impact is only a change toyour state file.
This command can be undone using the "terraform untaint" command with the same address.

`terraform taint docker_container.nginx-server[0]`{{execute}}
<pre>
terraform taint docker_container.nginx-server[0]
</pre>

Subsequent plan and apply commands will delete and recreate the nginx container due to this taint.

Another useful state related command is 'terraform console'. This is an interactive shell which can operate on the statefile using HCL, 
and can help with developing interpolation.

`terraform console`{{execute}}
<pre>
> docker_container.nginx-server[0].ports[0].external
32768
</pre>

Use Control-D to exit the console.
