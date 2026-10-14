# خدمة فتيات إعدادي

نسخة من برنامج الحضور (Hdour) لخدمة فتيات إعدادي، بنفس الشكل والمواصفات، لكن على **مشروع Firebase جديد ومنفصل تمامًا**.
الفصول الافتراضية: أولى إعدادي، تانية إعدادي، تالتة إعدادي (بتتعمل أوتوماتيك أول مرة الأدمن يدخل، وتقدر تعدّلها من جوه البرنامج).

## الإعداد (مرة واحدة)

بيانات مشروع Firebase (`e3taty`) متحطوطة فعلاً في `index.html`. اللي فاضل:

1. من [Firebase console](https://console.firebase.google.com) افتح مشروع `e3taty` → Build → **Authentication** → Sign-in method: فعّل **Email/Password**.
2. من Build → **Firestore Database**: اعمل Database (production mode) لو لسه معملتهاش.
3. من Firestore → **Rules**: امسح الموجود والصق محتوى ملف `firestore.rules` وادوس Publish.
4. افتح `index.html` وابحث عن `ADMIN_EMAILS` وحط إيميل الأدمن (ولازم يبقى نفسه في `firestore.rules` جوه دالة `isPrimaryAdminEmail`، وبعد أي تغيير في الملف اعمله Publish من Firebase console).
5. ارفع الملفات على GitHub repo جديد وفعّل GitHub Pages، وبعدها أضف رابط الموقع (مثلاً `username.github.io`) في Authentication → Settings → **Authorized domains**.
6. ادخل الموقع وسجّل حساب الأدمن **الأول** بإيميل الأدمن، وبعده الخدام التانيين.

## ملاحظات

- مفيش أي بيانات اتنقلت من برنامج Hdour القديم: القاعدة جديدة وفاضية.
- App Check اختياري: لو فعّلته في Firebase حط الـ Site key في `RECAPTCHA_SITE_KEY` جوه `index.html`.
- الأيقونات هي نفس أيقونات البرنامج الأصلي، بدّلها (`icon-193.png` و`icon-513.png`) لو عايز شكل مختلف.
