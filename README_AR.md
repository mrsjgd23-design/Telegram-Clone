# 🚀 مشروع Telegram Clone - دليل الإعداد الكامل

## 📋 المحتويات
1. [نظرة عامة](#نظرة-عامة)
2. [المتطلبات](#المتطلبات)
3. [التثبيت](#التثبيت)
4. [الإعداد](#الإعداد)
5. [التشغيل](#التشغيل)
6. [حل المشاكل](#حل-المشاكل)

---

## 🎯 نظرة عامة

هذا مشروع استنساخ لتطبيق Telegram يوفر:
- ✅ التسجيل وتسجيل الدخول
- ✅ الدردشة الفورية
- ✅ إرسال الصور والرسائل الصوتية
- ✅ المكالمات الصوتية والمرئية
- ✅ Theme فاتح وداكن

---

## 📦 المتطلبات

قبل البدء، تأكد من تثبيت:
- **Node.js** (الإصدار 14 أو أعلى)
- **npm** (يأتي مع Node.js)
- **MongoDB Atlas** حساب (مجاني)

---

## 🛠️ التثبيت

### الخطوة 1: تنزيل المشروع
```bash
# إذا كنت تستخدم git
git clone https://github.com/mrsjgd23-design/Telegram-Clone.git
cd Telegram-Clone

# أو قم بفك ضغط الملف المحمل
```

### الخطوة 2: تثبيت Dependencies الرئيسية
```bash
npm install
```

### الخطوة 3: تثبيت Dependencies للعميل (React)
```bash
cd client
npm install
cd ..
```

---

## ⚙️ الإعداد

### إنشاء ملف .env

أنشئ ملف جديد باسم `.env` في المجلد الرئيسي وأضف:

```env
PORT=4000
MONGO_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@cluster0.xxxxx.mongodb.net/telegram_clone_db?retryWrites=true&w=majority&appName=Cluster0&serverSelectionTimeoutMS=30000&socketTimeoutMS=45000
JWT_SECRET_KEY=your-very-secure-secret-key-here-change-this
JWT_EXPIRES_IN=90
CLOUDINARY_NAME=your-cloudinary-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret
```

### ⚠️ ملاحظات مهمة للإعداد:

#### 1. إعداد MongoDB:
- سجل حساب مجاني في [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- أنشئ Cluster جديد
- اضغط على "Connect" → "Connect your application"
- انسخ Connection String
- **مهم جداً:** إذا كانت كلمة المرور تحتوي على حروف خاصة، يجب ترميزها:
  - `@` → `%40`
  - `#` → `%23`
  - `$` → `%24`
  - `%` → `%25`
  
  **مثال:**
  - كلمة المرور الأصلية: `myPass@123`
  - في الـ URI: `myPass%40123`

#### 2. إعداد Cloudinary (اختياري):
- سجل حساب مجاني في [Cloudinary](https://cloudinary.com/)
- من Dashboard، انسخ:
  - Cloud Name
  - API Key
  - API Secret

---

## 🚀 التشغيل

### التشغيل للمرة الأولى:

#### 1. بناء تطبيق React:
```bash
cd client
npm run build
cd ..
```

⏱️ **ملاحظة:** عملية البناء قد تستغرق 1-3 دقائق

#### 2. تشغيل السيرفر:
```bash
npm start
```

✅ عند رؤية الرسائل التالية، يكون التطبيق جاهزاً:
```
Listening...
Database connected...
```

#### 3. افتح المتصفح:
```
http://localhost:4000
```

---

## 🎨 استخدام التطبيق

### إنشاء حساب جديد:
1. افتح التطبيق في المتصفح
2. اضغط على "New to Telegram"
3. املأ البيانات:
   - **الاسم:** اسمك الكامل
   - **Username:** اسم مستخدم فريد (بالإنجليزية)
   - **كلمة المرور:** 8 أحرف على الأقل
   - **تأكيد كلمة المرور:** نفس كلمة المرور
4. اضغط على "JOIN"

### تسجيل الدخول:
1. أدخل Username
2. أدخل كلمة المرور
3. اضغط على "LOGIN"

---

## 🔧 حل المشاكل

### المشكلة: خطأ "secretOrPrivateKey must have a value"

**الحل:**
1. تأكد من وجود ملف `.env` في المجلد الرئيسي
2. تأكد من وجود `JWT_SECRET_KEY` في الملف
3. أعد تشغيل السيرفر

```bash
# أوقف السيرفر (Ctrl+C)
npm start
```

---

### المشكلة: خطأ "MongoServerError: duplicate key error"

**الحل:** اسم المستخدم موجود مسبقاً، استخدم اسم مستخدم مختلف

---

### المشكلة: "Database connection timeout"

**الحل:**
1. تحقق من صحة MONGO_URI في ملف `.env`
2. تأكد من ترميز الأحرف الخاصة في كلمة المرور
3. تحقق من اتصالك بالإنترنت
4. تأكد من إضافة عنوان IP الخاص بك في MongoDB Atlas:
   - افتح MongoDB Atlas
   - اذهب إلى Network Access
   - اضغط "+ ADD IP ADDRESS"
   - اختر "Allow Access from Anywhere" (0.0.0.0/0)

---

### المشكلة: الصفحة فارغة أو بيضاء

**الحل:** لم تقم ببناء تطبيق React

```bash
cd client
npm run build
cd ..
npm start
```

---

### المشكلة: "Port 4000 already in use"

**الحل:**

**على Windows:**
```bash
netstat -ano | findstr :4000
taskkill /PID <رقم_العملية> /F
```

**على Mac/Linux:**
```bash
lsof -ti:4000 | xargs kill -9
```

ثم شغل السيرفر مرة أخرى:
```bash
npm start
```

---

## 📚 الأوامر المفيدة

### تطوير Frontend فقط:
```bash
cd client
npm start
```
سيفتح على: `http://localhost:3000`

### إعادة بناء Frontend:
```bash
cd client
npm run build
cd ..
```

### تشغيل السيرفر فقط:
```bash
npm start
```

### تحديث Dependencies:
```bash
npm update
cd client
npm update
cd ..
```

---

## 🌐 النشر (Deployment)

### النشر على Heroku:
```bash
# تسجيل الدخول
heroku login

# إنشاء تطبيق
heroku create your-app-name

# إضافة متغيرات البيئة
heroku config:set MONGO_URI="your-mongo-uri"
heroku config:set JWT_SECRET_KEY="your-secret"

# النشر
git push heroku main
```

### النشر على Vercel:
1. قم بتحميل المشروع على GitHub
2. سجل في [Vercel](https://vercel.com)
3. اربط repository
4. أضف متغيرات البيئة في Settings
5. انشر المشروع

---

## 📱 الميزات المتاحة

✅ **التسجيل وتسجيل الدخول**
- إنشاء حساب جديد
- تسجيل الدخول بأمان
- JWT authentication

✅ **إدارة جهات الاتصال**
- إضافة جهات اتصال جديدة
- حذف جهات الاتصال
- البحث في جهات الاتصال

✅ **المحادثات**
- الدردشة الفورية
- إرسال الرموز التعبيرية (Emojis)
- إرسال الصور
- تسجيل وإرسال الرسائل الصوتية

✅ **المكالمات**
- مكالمات صوتية
- مكالمات فيديو
- سجل المكالمات

✅ **إعدادات المستخدم**
- تغيير الصورة الشخصية
- تحديث البيو
- Theme فاتح/داكن

✅ **Chatbot**
- التحدث مع Telegram Bot
- ردود تلقائية

---

## 🔒 الأمان

⚠️ **ملاحظات أمنية:**
1. **لا تشارك ملف `.env` أبداً**
2. غير `JWT_SECRET_KEY` إلى قيمة قوية وفريدة
3. استخدم كلمات مرور قوية لـ MongoDB
4. في الإنتاج، استخدم HTTPS دائماً
5. لا ترفع ملف `.env` إلى GitHub (محمي بـ .gitignore)

---

## 📞 الدعم

إذا واجهت أي مشاكل:
1. راجع قسم [حل المشاكل](#حل-المشاكل)
2. تحقق من ملف `.env`
3. تأكد من بناء React app
4. راجع logs السيرفر للأخطاء

---

## 📄 الترخيص

هذا المشروع مفتوح المصدر ومتاح للاستخدام الشخصي والتعليمي.

---

## 🙏 شكر خاص

- **المطور الأصلي:** Adekola Thanni
- **Repository:** [Telegram-Clone](https://github.com/AdekolaThanni/Telegram-Clone)

---

## ✅ Checklist - تأكد من:

قبل التشغيل:
- [ ] تم تثبيت Node.js و npm
- [ ] تم تثبيت dependencies (`npm install`)
- [ ] تم تثبيت dependencies للعميل (`cd client && npm install`)
- [ ] تم إنشاء ملف `.env` بالإعدادات الصحيحة
- [ ] تم ترميز كلمة مرور MongoDB بشكل صحيح
- [ ] تم بناء React app (`cd client && npm run build`)

عند التشغيل:
- [ ] السيرفر يعمل على port 4000
- [ ] رسالة "Database connected..." ظاهرة
- [ ] يمكن فتح التطبيق على http://localhost:4000
- [ ] يمكن إنشاء حساب جديد بنجاح

---

**🎉 مبروك! الآن لديك نسخة عاملة من Telegram Clone!**

للأسئلة أو المساعدة، راجع قسم حل المشاكل أعلاه.
