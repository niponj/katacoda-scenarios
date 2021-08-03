As our infrastructure grows and changes, terraform will manage and ensure we always have our defined desired state.

We can change the number of nginx containers by setting the container_count variable.

If we create a plan you will see the actions Terraform will need to apply to adapt our infrastructure to match our configuration.

`terraform plan -var 'container_count=2'`{{execute}}

In the plan output the delta changes are explained. You should carefully review the plan to be sure that the changes are in line with your expectations.

We can then apply the plan as we did in the previous step.

`terraform apply -var 'container_count=2'`{{execute}}

