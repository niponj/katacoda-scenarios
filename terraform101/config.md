Terraform ทำงานโดยใช้ configuration file ซึ่งส่วนหลักจะเป็น main.tf โดย configuation นี้ทำงานในรูปแบบไม่เจาะจงวิธีการ (declarative)โดยเขียนเพื่อสร้างผลลัพธ์ที่ต้องการให้เกิดขึ้น (desired state) บน infrastructure ที่กำหนด เช่น AWS cloud โดยคำสั่งทั้งหมดจะใส่ไว้ในไฟล์และไดเรกทรอรี่ที่มีนามสกุล .tf เพื่อใช้สร้าง configuration สำหรับป้อนเข้า terraform.

Config file ใช้โครงสร้างแบบง่าย แต่มีศักยภาพ ในรูปแบบ [HCL templating language](https://www.terraform.io/docs/configuration/syntax.html)

Resource คือองค์ประกอบย่อยของ infrastructure ที่เกี่ยวข้องกับ provider ตัวอย่างเช่น ถ้าใช้งาน docker บนเครื่องใดๆ จะมี container หรือ image เป็น resource ที่สร้างไว้ใน docker provider และจะใช้ในการกำหนด containers และ images จริงที่จะเกิดขึ้นหลังการสร้างจาก terraform อีกที

ในการเริ่มต้นนี้ เราจะทำการสร้าง infrastructure โดยกำหนด Docker ขึ้นมาจาก image และ container แต่ถ้าใครยังไม่รู้จักว่า Docker คืออะไร แนะนำให้ทำความรู้จักก่อน (อ้างอิง ข้างล่าง)
เริ่มจากกำหนด resource ของ Docker image ก่อน โดยมีค่าพารามิเตอร์อยู่ 2 ตัว ตัวแรกคือ TYPE และตัวที่สอง คือ NAME โดย TYPE เป็นการระบุว่า ข้อมูลชุดนี้เป็น docker_image และชือของ image ก็คือ nginx โดยชุดข้อมูลนี้อยู่ใน block ที่กำหนดภายใต้ {} นี้ จะมีพารามิเตอร์ คือ ชือ และ tag ของ Docker image.

<pre class="file" data-filename="main.tf" data-target="append">resource "docker_image" "nginx" {
  name = "nginx:1.11-alpine"
}
</pre>


ถัดมา เราก็จะกำหนด resource อันที่สอง ซึ่งคือ container โดยสร้าง type อีกอัน ชือ docker_container และตั้งชือว่า nginx-server จากนั้นกำหนด block เพื่อสร้างพารามิเตอร์ต่างๆ พร้อมอ้างอิงไปยัง resource ที่สร้างไว้แล้วข้างบน (image)

<pre class="file" data-filename="main.tf" data-target="append">resource "docker_container" "nginx-server" {
  count = "${var.container_count}"
  name = "nginx-server-${count.index+1}"
  image = "${docker_image.nginx.latest}"
  ports {
    internal = 80
  }
  volumes {
    container_path  = "/usr/share/nginx/html"
    host_path = "/home/scrapbook/tutorial/www"
    read_only = true
  }
}
</pre>


* ด้วยการใช้ HCL ทำให้เราเขียน Template โดยการแทรกค่าจาก resource อื่นๆ เข้ามาใน config ของเราได้ เช่นกรณีนี้ docker_container resource ของเรา มีการดึงค่าจากข้างบนลงมา สร้างเป็น image = "${docker_image.nginx.latest}"

* Count เป็นการกำหนตัวเลข เพื่อให้ง่ายในการสร้าง resource หลายๆ ครั้ง โดยตัวอย่างนี้จะใช้เพื่อสร้าง container เป็นจำนวนครั้ง เท่ากับค่าใน container_count ที่อยู่ในไฟล์ variables.tf

อ้างอิง

* ทำความรู้จักกับ Docker และ Software Container
https://medium.com/thothzocial-engineering/%E0%B8%97%E0%B8%B3%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%A3%E0%B8%B9%E0%B9%89%E0%B8%88%E0%B8%B1%E0%B8%81-docker-%E0%B9%81%E0%B8%A5%E0%B8%B0-software-container-c6338629da11
