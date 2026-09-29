# نسخة Vercel الجاهزة — نجوم السعيدة للسفريات والسياحة

هذه النسخة مهيأة للنشر على **Vercel** باستخدام Next.js + React + PostgreSQL + Drizzle.

## النشر من الجوال فقط

### 1) ارفع المشروع إلى GitHub
- فك الضغط عن الملف على الهاتف باستخدام ZArchiver أو أي مدير ملفات.
- أنشئ Repository جديداً على GitHub.
- ارفع **محتويات مجلد المشروع** إلى المستودع، وليس ملف ZIP نفسه.
- لا ترفع `node_modules` أو `.env`.

### 2) اربط GitHub مع Vercel
- افتح Vercel وسجّل الدخول بحساب GitHub.
- اختر **Add New → Project** ثم مستودع المشروع.
- اترك Framework على Next.js.
- اترك Build Command على `npm run build`.
- اضغط Deploy بعد إضافة متغيرات البيئة المطلوبة.

### 3) قاعدة البيانات PostgreSQL
المشروع يحتاج PostgreSQL لأن الحجوزات والوجهات ولوحة الإدارة تعتمد على قاعدة البيانات.

ضع قيمة الاتصال في متغير:

`DATABASE_URL`

يمكن استخدام مزود PostgreSQL متوافق مع Vercel، بشرط أن يعطيك connection string صالحاً لـ `pg`.

### 4) متغيرات البيئة المطلوبة في Vercel
أضف المتغيرات التالية من **Project → Settings → Environment Variables**:

- `DATABASE_URL` — رابط اتصال PostgreSQL.
- `ADMIN_PASSWORD` — كلمة مرور لوحة الإدارة، 10 أحرف أو أكثر.
- `ADMIN_SECRET` — سر عشوائي بطول 32 حرفاً أو أكثر.
- `NEXT_PUBLIC_SITE_URL` — رابط الموقع النهائي، مثل رابط نطاق Vercel أو نطاقك الخاص.

يمكنك استخدام `.env.example` كمرجع فقط. لا ترفع ملف `.env` الحقيقي إلى GitHub.

### 5) قاعدة البيانات والبيانات الأولية
التطبيق يحتوي على تهيئة تلقائية للجداول والبيانات الأولية عند أول استخدام لطبقة البيانات، لذلك لا تحتاج إلى تنفيذ أمر Drizzle يدوياً قبل أول تشغيل إذا كانت قاعدة PostgreSQL فارغة.

> تأكد من أن `DATABASE_URL` صحيح وقاعدة البيانات تسمح باتصالات PostgreSQL من Vercel.

### 6) بعد النشر
اختبر من الهاتف:
- الصفحة الرئيسية `/`
- الوجهات `/destinations`
- الحجز `/booking`
- متابعة الحجز `/my-bookings`
- تسجيل الإدارة `/admin/login`
- فحص الصحة `/api/health`

## ملاحظات مهمة

- لا تستخدم Static Export؛ الموقع يحتاج Server-Side Next.js وAPI وقاعدة PostgreSQL.
- لا ترفع `node_modules`.
- لا ترفع `.env` أو أي كلمات مرور/أسرار إلى GitHub.
- عند تغيير متغيرات البيئة في Vercel، أعد النشر لتطبيقها على Deployment جديد.
- `NEXT_PUBLIC_SITE_URL` يفضل أن يكون رابط الموقع النهائي حتى تكون canonical/SEO صحيحة.
