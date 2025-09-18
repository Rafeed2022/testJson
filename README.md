<<<<<<< HEAD
# test
=======
# استضافة الصفحة عبر GitHub Pages (دليل سريع)

هذه الصفحة أحادية الملف (`index.html`) جاهزة للعرض ويمكن استضافتها مباشرة عبر GitHub Pages. أدناه خطوات سريعة باللغة العربية مع أوامر PowerShell قابلة للنسخ.

## خيار 1 — رفع المشروع إلى مستودع جديد على GitHub (سهل)
1. أنشئ مستودعًا جديدًا على GitHub (مثلاً `my-products-site`).
2. في مجلد المشروع المحلي (`d:\vscode\onPageWeb`) افتح PowerShell ثم شغّل الأوامر التالية:

```powershell
# تهيئة المستودع محليًا وإضافة الملفات
git init
git add .
git commit -m "Initial commit: products site"
# غيّر URL إلى رابط المستودع الذي أنشأته على GitHub
git remote add origin https://github.com/<username>/<repo>.git
git branch -M main
git push -u origin main
```

3. اذهب لصفحة المستودع على GitHub > Settings > Pages.
4. ضمن Source اختر Branch = `main` وFolder = `/ (root)` ثم اضغط Save.
5. بعد ثوانٍ (أو دقائق) سيظهر رابط موقع GitHub Pages (مثل `https://<username>.github.io/<repo>/`). افتح هذا الرابط وسترى `index.html` معروضًا.

## خيار 2 — استخدام الفرع `gh-pages` (بدون إعداد Pages في الواجهة)
يمكنك استخدام أداة نشر تلقائي (مثل `gh-pages` عبر npm) أو دفع الفرع `gh-pages` يدوياً. خطوات سريعة:

```powershell
# إنشاء فرع gh-pages ورفع محتواه
git checkout --orphan gh-pages
git --work-tree . add --all
git --work-tree . commit -m "Deploy to gh-pages"
git push origin gh-pages --force
git checkout main
```

ثم اختر في Settings > Pages المصدر `gh-pages` كـ Branch.

## ملاحظة عن ملف JSON وCORS
- إذا استخدمت رابط `https://raw.githubusercontent.com/.../products-mock.json` فالطلب عادة ما يعمل من GitHub Pages (CORS مدعوم عادةً).
- إذا واجهت خطأ CORS في المتصفح (عند fetch)، فالحلول:
  - استضف ملف `products-mock.json` ضمن نفس المستودع وادعمه عبر Pages (ثم استخدم رابط نسبي مثل `/products-mock.json`).
  - أو قدّم الملف من خدمة تدعم CORS مثل GitHub Pages أو S3 مع تهيئة رأس `Access-Control-Allow-Origin: *`.

## روابط مفيدة
- GitHub Pages docs: https://docs.github.com/en/pages
- Raw GitHub example: https://raw.githubusercontent.com/<username>/<repo>/main/products-mock.json

## احتياطات
- عند فتح `index.html` محليًا عبر `file://` قد تمنع بعض المتصفحات طلبات `fetch`. استعمل خادم محلي (مثل `python -m http.server`) أو استضف عبر Pages كما في الأعلى.

إذا تريد، أستطيع:
- تحديث `index.html` لاستخدام رابط JSON نسبي `/products-mock.json` بدل رابط GitHub Raw (يوفر أفضل توافق عند استضافة عبر Pages).
- أو أساعدك في خطوة بخطوة برفع المستودع (لو أعطيتني اسم المستخدم واسم المستودع الذي تريده).
>>>>>>> 39e484c (Initial commit: onPageWeb single-file product page + mock JSON + README)
