To destroy the infrastructure, use the CLI

`terraform destroy`{{execute}}

* The destroy must be confirmed unless the  -force or  -auto-approve command option is used
* Reads state, marks resources for deletion
* Issues API calls to providers to meet the desired state
* Obvious warning: this will destroy resources!
