# نجوم السعيدة — Next.js + React

نسخة الويب الإنتاجية مبنية بالكامل على Next.js وReact وTypeScript وPostgreSQL/Drizzle، مع PWA ولوحة إدارة.

## المتطلبات
- Node.js 20+
- PostgreSQL 14+
- npm

## التشغيل

```bash
npm ci
cp .env.example .env.local
npm run typecheck
npm run lint
npm run build
npm start
```

## متغيرات الإنتاج

يجب ضبط `DATABASE_URL` و`ADMIN_PASSWORD` و`ADMIN_SECRET` و`NEXT_PUBLIC_SITE_URL` قبل التشغيل. لا توجد كلمة مرور مدير افتراضية داخل الكود.

## ملاحظات
- المشروع لا يعتمد على Joomla أو PHP.
- المشروع لا يحتاج إلى Joomla أو PHP لتشغيل الواجهة.
- لا يتم تخزين `/api/*` أو `/admin/*` في Service Worker.
- يفضّل تشغيله خلف HTTPS مع PostgreSQL محمي بالشبكة.

## UI/UX Production Upgrade — 2026-09

تم رفع مستوى الواجهة لتصبح أقرب إلى منتج سفر تجاري احترافي:
- Hero جديد بهوية بصرية أقوى وCTA واضح.
- بطاقات خدمات ووجهات محسّنة مع micro-interactions.
- صفحة الوجهات: hero مختصر، بحث وفلاتر أوضح، حالات empty state أفضل.
- صفحة الحجز: مقدمة مرئية + تسلسل خطوات أوضح.
- لوحة الإدارة: مركز عمليات بواجهة إحصاءات وبطاقات أكثر وضوحًا.
- صفحة تسجيل الإدارة: تصميم أمني أكثر احترافية.
- `next/image` للصور الرئيسية والوجهات لتحسين التحميل والصور المتجاوبة.
- Open Graph / Twitter metadata.
- JSON-LD لـ TravelAgency والوجهات.
- `sitemap.ts` و`robots.ts`.
- دعم `prefers-reduced-motion`.
- تحسين transitions وhover/press states.
- تحسين Next.js image optimization و`optimizePackageImports` لـ lucide-react.

### التحقق
- تم فحص الشيفرة بحثًا عن أخطاء TypeScript syntax ولم تظهر أخطاء parsing.
- `npm install` لم يكتمل داخل بيئة الفحص بسبب timeout للشبكة؛ لذلك يجب تشغيل `npm ci`/`npm install` ثم `npm run typecheck`, `npm run lint`, `npm run build` في بيئة متصلة.
