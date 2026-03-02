# Ai Sport Website

เว็บไซต์สำหรับ Ai Sport - ระบบจัดการสินค้าและรีวิวลูกค้า

## Features

- 🛍️ **จัดการสินค้า**: เพิ่ม/แก้ไข/ลบสินค้า พร้อมอัปโหลดรูปภาพ
- ⭐ **รีวิวและคะแนนดาว**: ลูกค้าสามารถส่งรีวิวและให้คะแนนดาว (1-5) ได้
- 👤 **ระบบผู้ใช้**: แยก Admin และ Customer
- 📱 **Responsive Design**: รองรับทั้ง Desktop และ Mobile

## Tech Stack

- **Backend**: Python Flask
- **Database**: PostgreSQL (via psycopg2)
- **Frontend**: HTML, CSS, JavaScript (Vanilla)
- **File Upload**: รองรับการอัปโหลดรูปภาพสินค้าและรีวิว

## Installation

1. **Clone repository**
```bash
git clone <repository-url>
cd "Ai Sport"
```

2. **Install dependencies**
```bash
pip install flask psycopg2-binary werkzeug
```

3. **Setup database**
- สร้าง PostgreSQL database
- แก้ไข connection string ใน `pyhon.py` (ฟังก์ชัน `get_connection()`)

4. **Initialize database**
```bash
python -c "from pyhon import init_db; init_db()"
```

5. **Create first admin**
```bash
# ใช้ API หรือแก้ไขโค้ดเพื่อสร้าง admin คนแรก
curl -X POST http://localhost:5000/api/setup/first-admin \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "your_password", "phone": "020xxxxxxxx"}'
```

6. **Run application**
```bash
python app.py
```

7. **Access**
- Frontend (Client): `http://localhost:5000/client/`
- Admin Dashboard: `http://localhost:5000/product`
- API: `http://localhost:5000/api/`

## Project Structure

```
Ai Sport/
├── app.py                 # Flask application (main server)
├── pyhon.py              # Database functions & models
├── client/               # Frontend files (static HTML/CSS/JS)
│   ├── index.html        # หน้าหลัก
│   ├── products.html     # หน้าสินค้า
│   ├── products-review.html  # หน้ารีวิว
│   ├── style.css         # Stylesheet
│   └── script.js         # JavaScript
├── templates/            # Server-side templates
│   ├── product.html      # Admin product management
│   └── dashboard.html    # Admin dashboard
├── static/               # Static files
│   ├── js/               # JavaScript modules
│   └── uploads/          # Uploaded images
└── README.md
```

## API Endpoints

### Public APIs (ไม่ต้องล็อกอิน)
- `GET /api/products` - รายการสินค้า
- `GET /api/reviews` - รายการรีวิว
- `POST /api/reviews` - ส่งรีวิวและคะแนนดาว (ลูกค้า)
- `PUT /api/reviews/<id>` - แก้ไขคะแนนดาว (เฉพาะเจ้าของรีวิว)

### Admin APIs (ต้องส่ง token)
- `GET /api/admin/products` - จัดการสินค้า
- `POST /api/admin/products` - เพิ่มสินค้า
- `PUT /api/admin/products/<id>` - แก้ไขสินค้า
- `DELETE /api/admin/products/<id>` - ลบสินค้า
- `GET /api/admin/reviews` - จัดการรีวิว
- `POST /api/admin/reviews` - เพิ่มรีวิว (Admin)
- `PUT /api/admin/reviews/<id>` - แก้ไขรีวิว
- `DELETE /api/admin/reviews/<id>` - ลบรีวิว

## Features Detail

### ระบบรีวิว
- ลูกค้าสามารถส่งรีวิวพร้อมคะแนนดาว (1-5) ได้โดยไม่ต้องล็อกอิน
- ลูกค้าสามารถแก้ไขคะแนนดาวของตัวเองได้ (ต้องใส่ชื่อให้ตรง)
- Admin สามารถจัดการรีวิวทั้งหมดได้

### ระบบสินค้า
- Admin สามารถเพิ่ม/แก้ไข/ลบสินค้าได้
- รองรับการอัปโหลดรูปภาพสินค้า
- แสดงสินค้าในหน้า Client

## License

Private project - All rights reserved

## Contact

AI SPORT
