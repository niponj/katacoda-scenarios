
ขั้นตอนต่อมา คือการเช็คว่า configuration ที่สร้างมามีความผิดพลาดหรือไม่ พร้อมตรวจทานกับ providers ว่าได้ทำทำ intiataion ครบถ้วน เทียบได้กับการตรวจแกรมม่าภาษาอังกฤษ

`terraform validate`{{execute}}


Once the configuration has been defined we need to create an execution plan. Terraform describes the actions required to achieve the desired state. The plan can be saved using -out. We'll apply the execution plan in the next step.

* Reads Terraform configuration, reads statefile (if it exists), computes a plan of changes required to meet desired state
* Optionally write plan to disk + run later
* Best practice: always run plan before apply and inspect plan 

To create a plan, use the CLI

`terraform plan`{{execute}}

The output of the command indicates the changes. In this case, you'll see a _+ dockercontainer.nginx-server and _+ dockerimage.nginx to highlight adding the new resources. Finally a summary of Plan: 2 to add, 0 to change, 0 to destroy.

Variables can be overridden using command line arguments
`terraform plan -var 'container_count=5'`{{execute}}

Alternatively, variables can be overridden using a tfvars file to pass the value.  Here, the file dev.tfvars contains ovrriding variable values. Also, the plan is output is stored for subsequent use with an apply:

<pre class="file" data-filename="dev.tfvars" data-target="replace">container_count=3
</pre>

`terraform plan -var-file=dev.tfvars -out dev.tfplan`{{execute}}
