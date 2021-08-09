เมื่อสร้าง terraform project แล้ว ก็ต้องทำการ initialize ซึ่งทำได้โดยใช้คำสั่งใน CLI ดังนี้

`terraform init`{{execute}}

เมื่อสั่งงานแล้ว จะเป็นการสร้าง .terraform directory ขึ้นมา แล้วทำการดาวน์โหลด plugins ที่จำเป็น พร้อมกับสร้าง remote state backend ขั้นมาถ้ามีการกำหนดไว้
