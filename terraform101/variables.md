
Variables คือตัวแปรที่ใช้เป็นอินพุต เพื่อป้อนสู่ terraform configuration

<pre class="file" data-filename="variables.tf" data-target="replace">variable "container_count" {
 type = number
 description = "The number of nginx containers to run"
 default = 1
}
</pre>

* resource ใช้วิธีดึงตัวเลขนี้จาก variable ข้างบนโดยใช้
<pre>count = "${var.container_count}"</pre>

* ทั้งนี้ ค่าของ variables ต้องถูกกำหนดไว้ก่อนที่จะมีการใช้งาน (หรือตั้งค่าเริ่มต้นไว้)
* variables values must be initialised before they are used (or defaulted).
