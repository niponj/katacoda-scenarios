โครงสร้างของแต่ละงาน ที่ใช้กับ terraform จะจัดเก็บในรูปแบบของไฟล์ และไดเร็กทอรี่ โดยจะแยกกลุ่มเป็น project ต่างๆ
โดยไฟล้หลักที่จะใช้งานที่เก็บ configuration (HCL) จะมีนามสกุล .tf ได้แก่ main.tf ซึ่งแม้จะตั้งชื่อเองได้ แต่มักจะตั้งชือตามตัวอย่าง
นอกเหนือจาก .tf ที่เก็บ configuration แล้ว ยังไฟล์ และไดเร็กทรอรี่อื่นๆ ที่สำคัญ ได้แก่
In addition to .tf configuration files, other files in the directory include:
* .terraform: เป็นไดเร็กทอรี่ ทีใช้เก็บ providers binaries ซึ่งเป็นไฟล์ที่ถูกดาวโหลดในขั้นตอน init
* variables.tf: เป็นไฟล์ ที่ใช้รวบรวมตัวแปร (variables) เหมือนการป้อนค่า input เข้าสู่่ configuration.
* outputs.tf: เป็นไฟล์ ที่ใช้รวบรวม ข้อมูลผลลัพธุ์จากการสั่งการ
* .tfvars: เป็นไฟล์ ที่ใช้เก็บค่าตัวแปร คล้าย variables.tf แต่จะใช้งานเงื่อนไขพิเศษ เช่น ใช้ทดสอบเงื่อนไขด้วยตัวแปร มักใช้ในขั้นตอนการ plan

ข้อแนะนำการใช้งาน
* ให้เก็บไฟล์และไดเร็กทอรี่ ที่เป็น project ต่างๆแยกไว้คนละชุด ตามตัวอย่าง 
* แต่ละไดเร็กทอรี่ จะมีการเก็บ state file ไว้ของใครของมัน
* ให้ใช้ชื่อไฟล์ ตามที่แนะนำในตัวอย่าง ได้แก่  main.tf, variables.tf, outputs.tf

<pre>├── nginx
│   ├── dev.tfvar
│   ├── main.tf
│   └── variables.tf
├── database
│   ├── main.tf
│   ├── mysql.tf
│   ├── variable_overrides.tfvar
│   └── variables.tf
└── network
    ├── main.tf
    ├── net-peering.tf
    ├── variable_overrides.tfvar
    └── variables.tf
</pre>

จากตัวอย่าง ไฟล์และไดเร็กทอรี่ ใน lab ได้ทำการสร้าง ngix directory สำหรับใช้เป็น project ตัวอย่าง และให้คุณได้เริ่มทดลองได้จากไดเร็กทอรีนั้นแล้ว
