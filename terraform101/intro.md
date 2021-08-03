ใน course เริ่มต้นนี้ เราจะเรียนรู้วิธีการทำงานพื้นฐานของ Hashicorp Terraform กัน

โดยใน Lab จะมีการเกรินนำ ทำความรู้จักส่วนสำคัญต่างๆ ของ Terraform ที่จำเป็นต้องรู้ รวมถึงวิธีการติดตั้งอย่างง่าย และใช้งาน commands ที่สำคัญ ซึงเมื่อทำตาม จะทำให้เข้าใจลำดับการทำงานได้ง่าย (Workflows)

อะไรคือ Terraform

* เป็นเครื่องมือ Infrastrure-As-Code หรือย่อว่า Iac ที่ใช้การติดต่อกับ APIs ไปยังบริการต่างๆ จากผู้ให้บริการ (Providers) เช่น Amazon AWS เพื่อใช้ในการจัดสรรร (Provisioning) และการจัดการระบบโครงสร้าง (Infrastructure Managemetn)
* An Infrastructure-As-Code (IaC) tool which leverages APIs provided by multiple service providers in order to provision and manage infrastructure
* ใช้รูปแบบการเขียนโดยไม่เจาะจงวิธีการ (Declarative) - โดยผู้ใช้ จะเขียน templates ต่างๆ เพื่อธิบายผลลัพธ์ที่ต้องการให้เกิดขึ้น (Desired end-state) แล้วให้ Terraform ทำการหาวิธ๊ในการทำให้เกิดผลลัพธ์นั้นเอง
* ใช้รูปแบบในการเขียนที่เป็นภาษาอย่างง่าย แต่มีศักยภาพ โดยใช้ HCL ซึ่งย่อมาจาก Hashicorp Configuration Languages
* ไม่ได้ยึดติดกับ Platform ใดๆ รองรับระบบคลาวด์ใหญ่ๆ ได้หมด รวมทั้ง IaaS, PaaS, SaaS ของแต่ละผู้ให้บริการ (ดูอ้างอิงเพิ่่มเติม)
* ช่วยให้งานวางระบบ Infrastructure ทำในรูปแบบที่ไม่ให้มีการแก้ไขได้ (Immutable) (ดูอ้างอิงเพิ่่มเติม)
* ง่ายในการจัดการแบบอัตโนมัติ
* เป็นเครื่องมือแบบ Open Source มีชุมชนช่วยให้คำแนะนำปรึกษา และมีการสนับสนุนแบบองค์กรด้วย (Enterprise Support) 

ความรู้พื้นฐานที่ควรมี ด้าน Cloud Computing 
https://techforteam.com/blog/what-is-cloud/

อ้างอิง
https://medium.com/@krittaboon.t/programming-paradigm-imperative-vs-declarative-3f34a34838c3
https://dev.to/peepeepopapapeepeepo/terraform-ep1-what-and-why-2hco
