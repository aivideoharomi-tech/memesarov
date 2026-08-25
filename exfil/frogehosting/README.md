# FrogeHosting 🐸

Minecraft server hosting uchun Django asosidagi backend + frontend (server-side render qilingan shablonlar).

## Xususiyatlari

- Tariflar (Plan) bilan landing sahifa
- Ro'yxatdan o'tish / kirish / chiqish (Django auth)
- Shaxsiy kabinet — foydalanuvchining serverlari ro'yxati
- Tarif tanlab, yangi Minecraft server buyurtma qilish
- Server tafsilotlari sahifasi
- Django admin panel orqali tariflar va serverlarni boshqarish

## O'rnatish

```bash
# 1. Virtual muhit yaratish
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

# 2. Kutubxonalarni o'rnatish
pip install -r requirements.txt

# 3. Ma'lumotlar bazasini tayyorlash
python manage.py migrate

# 4. Standart tariflarni yuklash (Tadpole, Frog, Bullfrog)
python manage.py loaddata plans

# 5. Admin foydalanuvchi yaratish
python manage.py createsuperuser

# 6. Serverni ishga tushirish
python manage.py runserver
```

Saytga http://127.0.0.1:8000 orqali kiring.
Admin panel: http://127.0.0.1:8000/admin

## Loyiha tuzilishi

```
frogehosting/
├── manage.py
├── frogehosting/        # loyiha sozlamalari (settings, urls, wsgi/asgi)
└── core/                 # asosiy ilova
    ├── models.py          # Plan, Server
    ├── views.py           # home, register, dashboard, order_server, server_detail
    ├── forms.py           # RegisterForm, ServerOrderForm
    ├── urls.py
    ├── admin.py
    ├── templates/core/    # HTML shablonlar (frontend)
    ├── static/core/       # CSS
    └── fixtures/plans.json
```

## Keyingi qadamlar (ixtiyoriy)

- To'lov tizimini ulash (Payme, Click, Stripe)
- Haqiqiy server provisioning (Docker/Pterodactyl API bilan integratsiya)
- Email orqali tasdiqlash va parolni tiklash
- REST API (Django REST Framework) qo'shish, agar mobil ilova yoki SPA frontend kerak bo'lsa
