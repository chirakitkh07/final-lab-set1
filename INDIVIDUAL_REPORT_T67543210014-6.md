# INDIVIDUAL REPORT

## ข้อมูลผู้จัดทำ
ชื่อ-นามสกุล: นายจิรกิตติ์ คำป่าตัน  
รหัสนักศึกษา: 67543210014-6  
กลุ่ม: SEC2-GROUP4

---

## ขอบเขตงานที่รับผิดชอบ

- Auth Service (Login, JWT)
- Task Service (CRUD Tasks)
- Log Service (รับและแสดง logs)
- Nginx (API Gateway, HTTPS, Rate Limit)
- Docker Compose (เชื่อมทุก service)

---

## สิ่งที่ได้ดำเนินการด้วยตนเอง

- เขียน API สำหรับ login และ generate JWT
- พัฒนา middleware สำหรับตรวจสอบ JWT
- พัฒนา CRUD API ใน Task Service
- เขียนระบบส่ง log จาก service ไปยัง Log Service
- ตั้งค่า Nginx ให้เป็น reverse proxy และเปิดใช้งาน HTTPS
- ตั้งค่า rate limiting ใน Nginx
- เชื่อมต่อ PostgreSQL กับทุก service
- ทดสอบ API ผ่าน Postman

---

## ปัญหาที่พบและวิธีการแก้ไข

### 1. ปัญหา JWT หมดอายุ (jwt expired)
- สาเหตุ: ใช้ token เก่าที่หมดอายุแล้ว
- วิธีแก้: login ใหม่เพื่อรับ token ใหม่ และกำหนดเวลา expires ให้เหมาะสม

### 2. ปัญหา Rate Limit ไม่ทำงาน
- สาเหตุ: ตั้งค่า rate สูงเกินไป (30r/s)
- วิธีแก้: ปรับเป็น 1r/s และ restart Docker ใหม่

### 3. ปัญหา Nginx ไม่ส่ง Authorization header
- สาเหตุ: ไม่มีการตั้งค่า proxy header
- วิธีแก้: เพิ่ม proxy_set_header Authorization

---

## สิ่งที่ได้เรียนรู้จากงานนี้

- เข้าใจการออกแบบ Microservices Architecture
- เข้าใจการทำงานของ JWT (Authentication Flow)
- เรียนรู้การใช้ Nginx เป็น API Gateway และ TLS termination
- เข้าใจการใช้ Docker Compose ในการรวมหลาย service
- เข้าใจการทำ Logging ผ่าน service แยก
- เรียนรู้การ debug ระบบหลาย service

---

## แนวทางการพัฒนาต่อไปใน Set 2

- เพิ่มระบบ Register และ User Service
- แยกฐานข้อมูลเป็น database per service
- Deploy ระบบขึ้น Cloud (Railway)
- เพิ่ม security เช่น refresh token
- ปรับปรุง logging ให้เป็น centralized logging system
