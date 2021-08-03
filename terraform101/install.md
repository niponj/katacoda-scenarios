
Terraform เขียนด้วยภาษา Go และมี CLI binary ให้ใช้งาน ติดตั้งได้ง่าย โดยวิธีการติดตั้งจะแตกต่างกันแล้วแต่ระบบ OS ซึ่งใน course นี้จะใช้การติดตั้งสำหรับ Ubuntu Linux โดยผู้เรียนสามารถดูขั้นตอนการติดตั้งได้ที่
https://www.terraform.io/downloads.html

## เริ่มต้นติดตั้ง Terraform
ทำการ download linux platform zip, unzip, แล้วย้าย files ไปที่ /usr/local/bin

`curl https://releases.hashicorp.com/terraform/0.12.5/terraform_0.12.5_linux_amd64.zip -O; unzip terraform_0.12.5_linux_amd64.zip; rm terraform_0.12.5_linux_amd64.zip; sudo mv terraform /usr/local/bin`{{execute}}

## ตรวจสอบ version ที่ติดตั้ง
`terraform version`{{execute}}
<pre>Terraform v0.12.5</pre>

## เช็คการใช้งาน โดยสั่งรัน
`terraform `{{execute}}

The most common cammands are plan and apply, but there a variety of commands to 
format, validate, refresh, and graph terraform config as well as tools to manage state and environment.
There is also support for an interactive console for Terraform interpolations.

You can find more about terraform on the official Hashicorp Terraform site at [https://www.terraform.io/](https://www.terraform.io)
