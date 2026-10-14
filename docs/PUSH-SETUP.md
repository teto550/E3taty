# تفعيل إشعارات الموبايل (Push) في E3taty

الكود جاهز في `index.html` و`sw.js` و`workers/push-worker.js` و`firestore.rules`. لحد ما تعمل الخطوات دي، الإشعارات بتفضل جوه التطبيق بس.
المشروع: Firebase `e3taty` (منفصل عن Hdour وSTMina، فالمفتاح والـ Worker ليهم هنا لوحدهم). كله على الخطط المجانية.

1. **القواعد:** انسخ محتوى `firestore.rules` في Firebase Console → Firestore → Rules → Publish (اتضاف `fcmTokens` لتعديل الخادمة لحسابها).
2. **مفتاح VAPID:** Project settings → Cloud Messaging → Web Push certificates → Generate key pair → انسخ المفتاح العام.
3. **Service account:** Project settings → Service accounts → Generate new private key → هينزل ملف JSON (متحطوش في الـ repo).
4. **Cloudflare Worker:** اعمل Worker جديد (مثلاً `e3taty-push`) والصق فيه محتوى `workers/push-worker.js`، وبعدين في Settings → Variables and Secrets:
   - `SERVICE_ACCOUNT` (Secret): محتوى ملف الـ JSON كله.
   - `ALLOWED_ORIGIN` (Text): `https://teto550.github.io`
   - `APP_URL` (Text): رابط تطبيق E3taty.
5. **في `index.html`:** املا `FCM_VAPID_KEY` (من خطوة 2) و`PUSH_WORKER_URL` (رابط الـ Worker) في قسم "إشعارات الموبايل الحقيقية".
6. **على الموبايل:** افتح التطبيق بحساب الأدمن → ⚙️ → 🔔 الإشعارات → دوس "دوس للتفعيل" واسمح بالإذن. على الآيفون لازم تضيف التطبيق للشاشة الرئيسية الأول.

بتوصل إشعارات للأدمن لـ: طلب انضمام جديد، وخادمة فتحت التطبيق (مرة كل 30 دقيقة للخادمة).
