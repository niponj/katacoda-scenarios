
* Provider คือ กลุ่มของผู้ให้บริการ หรือบริษัทที่ให้บริการใดๆ มีโครงสร้างเป็นโมดุล (modular) ที่ใช้แทน IaaS, SaaS และ PaaS ของแต่ละกลุ่ม เช่น AWS โดยการกำหนด provider มีประโยชน์เพื่อใช้การนำบริการต่างๆ มาประกอบใน project

* โดย Provider จะมีส่วนกอบจากส่วนย่อยที่เรียกใช้ APIs และ ทรัพยากร (resources) ต่างๆ ที่เอาเข้ามารวมกัน (packaged)

* ตัวอย่างของ providers ได้แก่ aws, azurerm, vmware, datadog และ docker ที่ถูกใช้ใน lab นี้

* ใน project ใดๆ สามารถอ้างอิงถึง providers มากกว่าหนึ่งตัวได้

* ทั้งนี้ จะมี provider มาตรฐาน และ providers ที่สร้างขึ้นเอง (thirdparty custom provider) อยู่มากมายให้เลือกใช้ ดังนี้
* [standard providers](https://www.terraform.io/docs/providers/index.html)

Providers จะถูกใส่ไว้ใน terraform config ซึ่งอยู่ในไฟล์ที่มีนามสกุล .tf ซึ่งจะมีการกำหนดค่า API endpoint, credentials ซึ่งเป็นรหัสสำหรับเข้าถึงบริการ, debug setting และค่าพารามิเตอร์อื่นๆ เพื่อใช้งาน API นั้นห

ในกรณีของ lab ที่เราจะทำ จะกำหนดค่า config file โดยใส่ provider ชื่อ docker พร้อมกับระบุ host ซึ่งกรณีนี้ ก็จะมาใช้เครื่องใน lab ของเรานั่นเอง

<pre class="file" data-filename="main.tf" data-target="replace">provider "docker" {
  host = "unix:///var/run/docker.sock"
}

</pre>

นอกจากใน project ใดๆ ที่ทำ จะใช้ providers มากว่าหนึ่งได้ (เช่น aws + azurerm) ถ้าเราอยากเอา provider ใดๆ แต่ให้มีหลายแบบ (instances) ก็ทำได้เช่นกัน โดยการกำหนด "alias" ของแต่ละ instance นั้น ทำให้สามารถใช้งาน เช่น สร้าง docker host หลายๆ เครื่อง หรือมี aws หลายๆ regions ได้
[Provider documentation](https://www.terraform.io/docs/configuration/providers.html)
