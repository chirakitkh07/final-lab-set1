# ENGSE207 Software Architecture  
## README — Final Lab Set 1: Microservices + HTTPS + Lightweight Logging

> เอกสารฉบับนี้ใช้เป็น `README.md` สำหรับ repository ของ **Final Lab Set 1**

---

## 1. ข้อมูลรายวิชาและสมาชิก

**รายวิชา:** ENGSE207 Software Architecture  
**ชื่องาน:** Final Lab — ชุดที่ 1: Microservices + HTTPS + Lightweight Logging  

**สมาชิกในกลุ่ม**
- นายจิรกิตติ์ คำป่าตัน 67543210014-6  
- นางสาวกฤตพร แหลมไทย 67543210051-8  

**Repository:** `final-lab-set1/`

---

## 2. ภาพรวมของระบบ

Final Lab ชุดที่ 1 เป็นการพัฒนาระบบ Task Board แบบ Microservices โดยเน้นหัวข้อสำคัญดังนี้

- การทำงานแบบแยก service
- การใช้ Nginx เป็น API Gateway
- การเปิดใช้งาน HTTPS ด้วย Self-Signed Certificate
- การยืนยันตัวตนด้วย JWT
- การจัดเก็บ log แบบ Lightweight Logging ผ่าน Log Service
- การเชื่อมต่อ Frontend กับ Backend ผ่าน HTTPS
---

## 3. วัตถุประสงค์ของงาน

- ออกแบบระบบแบบ Microservices
- ใช้ Nginx เป็น reverse proxy และ TLS
- ใช้ JWT authentication
- ออกแบบ logging flow
- ใช้ Docker Compose รวมระบบ

---

## 4. Architecture Overview

```
Browser / Postman
       │ HTTPS :443
       ▼
Nginx (API Gateway)
   ├── /api/auth/*  → auth-service
   ├── /api/tasks/* → task-service
   ├── /api/logs/*  → log-service
   └── /            → frontend
            │
            ▼
     PostgreSQL
```

---

## 5. โครงสร้าง Repository

```
final-lab-set1/
├── README.md
├── docker-compose.yml
├── nginx/
├── frontend/
├── auth-service/
├── task-service/
├── log-service/
├── db/
└── screenshots/
```

---

## 6. เทคโนโลยีที่ใช้

- Node.js / Express.js  
- PostgreSQL  
- Nginx  
- Docker  
- JWT  
- bcryptjs  

---

## 7. การรันระบบ

```
docker compose down -v
docker compose up --build
```

เปิด:
```
https://localhost
```

---

## 8. Seed Users

| Username | Email | Password | Role |
|---|---|---|---|
| alice | alice@lab.local | alice123 | member |
| bob | bob@lab.local | bob456 | member |
| admin | admin@lab.local | adminpass | admin |

---

## 9. API Summary

### Auth
- POST /api/auth/login

### Tasks
- GET /api/tasks
- POST /api/tasks
- PUT /api/tasks/:id
- DELETE /api/tasks/:id

### Logs
- GET /api/logs

---

## 10. Screenshots

- 01_docker_running.png  
- 02_https_browser.png  
- 03_login_success.png  
- 04_login_fail.png  
- 05_create_task.png  
- 06_get_tasks.png  
- 07_update_task.png  
- 08_delete_task.png  
- 09_no_jwt_401.png  
- 10_logs_api.png  
- 11_rate_limit.png  
- 12_frontend_screenshot.png  

---

## 11. System Architecture (Frontend & Backend)

### 🌐 Frontend
- แสดง UI
- Login / Task / Logs
- เรียก API ผ่าน Nginx

ตัวอย่าง:
```
fetch("/api/tasks", {
  headers: {
    Authorization: "Bearer " + token
  }
});
```

---

### ⚙️ Backend (Microservices)
#### Auth Service
- Login + JWT

#### Task Service
- CRUD Tasks

#### Log Service
- เก็บ logs

#### Nginx
- Routing
- HTTPS
- Rate limit

#### Database
- PostgreSQL (shared)

---

## 12. Flow การทำงาน

1. Login → ได้ token  
2. เรียก API ด้วย token  
3. Task service ตรวจ JWT  
4. บันทึก log  

---

## 13. ปัญหาที่พบ
- bcrypt hash ไม่ตรง → login ไม่ได้  
- JWT หมดอายุ  
- nginx route ผิด  
- rate limit ไม่ทำงาน  

---

## 14. ข้อจำกัด

- ใช้ self-signed cert  
- ใช้ shared DB  
- ไม่มี register  

---

## 15. สรุป

ระบบนี้แสดงให้เห็นการทำงานของ:
- Microservices  
- API Gateway  
- JWT Authentication  
- Logging System  
