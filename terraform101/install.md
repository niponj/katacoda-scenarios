
Terraform is a go binary CLI and is easy to install and use. The install instructions vary by platform, linux is assumed for this course.  See https://www.terraform.io/downloads.html

## Install terraform 
Download linux platform zip, unzip, move to /usr/local/bin

`curl https://releases.hashicorp.com/terraform/0.12.5/terraform_0.12.5_linux_amd64.zip -O; unzip terraform_0.12.5_linux_amd64.zip; rm terraform_0.12.5_linux_amd64.zip; sudo mv terraform /usr/local/bin`{{execute}}

## confirm version
`terraform version`{{execute}}
<pre>Terraform v0.12.5</pre>

## terraform usage
`terraform `{{execute}}

The most common cammands are plan and apply, but there a variety of commands to 
format, validate, refresh, and graph terraform config as well as tools to manage state and environment.
There is also support for an interactive console for Terraform interpolations.

You can find more about terraform on the official Hashicorp Terraform site at [https://www.terraform.io/](https://www.terraform.io)
