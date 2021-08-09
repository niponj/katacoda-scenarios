
Variables คือตัวแปรที่ใช้เป็นอินพุต เพื่อป้อนสู่ terraform configuration

<pre class="file" data-filename="variables.tf" data-target="replace">variable "container_count" {
 type = number
 description = "The number of nginx containers to run"
 default = 1
}
</pre>

* resources can access variable values in HCL:
<pre>count = "${var.container_countainer_count}"</pre>

* variables values must be initialised before they are used (or defaulted).
