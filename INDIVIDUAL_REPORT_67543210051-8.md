# INDIVIDUAL REPORT

## ข้อมูลผู้จัดทำ
ชื่อ-นามสกุล: นางสาวกฤตพร แหลมไทย  
รหัสนักศึกษา: 67543210051-8  
กลุ่ม: SEC2-GROUP4  

---

## ขอบเขตงานที่รับผิดชอบ

- Frontend (UI/UX)
- หน้า Login
- หน้า Task Board
- หน้า Log Dashboard
- เชื่อมต่อ Frontend กับ Backend API

---

## สิ่งที่ได้ดำเนินการด้วยตนเอง

- ออกแบบและพัฒนา UI หน้า Login
- พัฒนา Task Board สำหรับแสดงรายการ tasks
- เขียน JavaScript สำหรับเรียก API (fetch)
- จัดการ JWT token ใน frontend
- พัฒนา feature เพิ่ม / แก้ไข / ลบ task
- พัฒนา Log Dashboard สำหรับ admin
- ทดสอบการทำงานร่วมกับ backend

---

## ปัญหาที่พบและวิธีการแก้ไข

### 1. ปัญหาเรียก API ไม่ได้ (401 Unauthorized)
- สาเหตุ: ไม่ได้ส่ง JWT token ใน header
- วิธีแก้: เพิ่ม Authorization header ใน fetch

### 2. ปัญหา HTTPS ไม่สามารถเรียก API ได้
- สาเหตุ: browser block self-signed certificate
- วิธีแก้: กดยอมรับ certificate ใน browser

### 3. ปัญหาแสดงข้อมูลไม่ตรง user
- สาเหตุ: ใช้ token ของ user คนละคน
- วิธีแก้: ใช้ token เดียวกันในทุก request

---

## สิ่งที่ได้เรียนรู้จากงานนี้

- เข้าใจการเชื่อม Frontend กับ Backend ผ่าน API
- เข้าใจการใช้ JWT ในฝั่ง client
- เรียนรู้การใช้ fetch API
- เข้าใจการทำงานของ HTTPS และ certificate
- เข้าใจ flow ของระบบ Microservices

---

## แนวทางการพัฒนาต่อไปใน Set 2

- ปรับ UI ให้ responsive มากขึ้น
- เพิ่มระบบ register และ profile
- เชื่อมต่อกับ backend ที่ deploy บน cloud
- เพิ่ม error handling ใน frontend
- ปรับปรุง UX ให้ใช้งานง่ายขึ้น
