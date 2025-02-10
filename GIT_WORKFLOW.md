# 🚀 Git Workflow for SafarAI | دليل استخدام Git لمشروع SafarAI

This document explains the workflow for managing the **SafarAI** repository, covering the **Staging (Development)** and **Main (Production)** branches.

---

## 📌 Branching Strategy | استراتيجية الفروع

We use two main branches:

- **`staging`**: For active development, testing, and debugging.
- **`main`**: For stable, production-ready releases.

New features and fixes should always be developed in feature branches and merged into `staging` before reaching `main`.

---

## 🔄 Standard Git Workflow | سير عمل Git القياسي

### 1️⃣ **Cloning the Repository | استنساخ المستودع**

To clone the repository for the first time:

```sh
git clone https://github.com/SafarAI-ProjectHub/safar-ai.git
cd safar-ai
```

To ensure you're working on the correct branch:

```sh
git checkout staging
```

---

### 2️⃣ **Creating a Feature Branch | إنشاء فرع ميزة جديدة**

Before working on a new feature or bug fix:

```sh
git checkout staging
git pull origin staging  # Get the latest updates
git checkout -b feature-branch-name
```

Use meaningful names like:

- `feature-user-authentication`
- `fix-payment-gateway-bug`

---

### 3️⃣ **Committing Changes | حفظ التعديلات (Commit)**

Follow this format for commit messages:

```sh
git add .
git commit -m "🔧 [Feature] Add user authentication"
git push origin feature-branch-name
```

- Use `🔧 [Feature]` for new features.
- Use `🐛 [Fix]` for bug fixes.
- Use `🚀 [Enhancement]` for improvements.
- Use `📝 [Docs]` for documentation updates.

---

### 4️⃣ **Merging to Staging | دمج الفرع مع Staging**

Once your feature is ready and tested:

```sh
git checkout staging
git pull origin staging
git merge feature-branch-name
git push origin staging
```

Create a **Pull Request (PR)** on GitHub to review before merging into `main`.

---

### 5️⃣ **Deploying to Main | النشر إلى Main**

After testing on `staging`, merge into `main`:

```sh
git checkout main
git pull origin main
git merge staging
git push origin main
```

Deployment scripts will automatically update the production server.

---

### 6️⃣ **Keeping Your Local Copy Updated | تحديث نسختك المحلية**

```sh
git checkout staging
git pull origin staging
git checkout main
git pull origin main
```


### 7️⃣ **Deploying Code to Server | نشر الكود على السيرفر**

#### **Staging Deployment**
To deploy changes to the `staging` server:

```sh
ssh -i ~/.ssh/your-key.pem ubuntu@your-server-ip
cd /var/www/html/safar-ai-staging
git pull origin staging
php artisan migrate --force  # Run only if database changes exist
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
sudo systemctl restart apache2
```

#### **Main (Production) Deployment**
To deploy changes to the `main` (production) server:

```sh
ssh -i ~/.ssh/your-key.pem ubuntu@your-server-ip
cd /var/www/html/safar-ai
git pull origin main
php artisan migrate --force  # Run only if database changes exist
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
sudo systemctl restart apache2
```

---

Always work with the latest code to avoid conflicts.

---

## 🛠️ Useful Git Commands | أوامر Git المفيدة

| Command | Description |
|---------|------------|
| `git status` | Check the current status of changes. |
| `git branch` | List all branches. |
| `git checkout branch-name` | Switch to another branch. |
| `git fetch origin` | Get updates from the remote repo. |
| `git log --oneline` | View commit history in one line. |

---

## 🚀 Best Practices | أفضل الممارسات

✅ Always **work in feature branches** before merging to `staging`.  
✅ Use **clear commit messages** following the provided format.  
✅ Keep your **local repository updated** to avoid conflicts.  
✅ **Never push directly to `main`**, always go through `staging` first.  
✅ **Code reviews** are required before merging into `main`.  

---

# 🚀 دليل استخدام Git لمشروع SafarAI

يوضح هذا المستند تدفق العمل مع Git لمستودع **SafarAI**، ويشمل العمل مع فروع **Staging (التطوير)** و **Main (الإنتاج)**.

---

## 📌 استراتيجية الفروع

يتم استخدام فرعين أساسيين:

- **`staging`**: مخصص للتطوير النشط والاختبار وتصحيح الأخطاء.
- **`main`**: مخصص للإصدارات المستقرة الجاهزة للإنتاج.

يجب تطوير الميزات الجديدة والإصلاحات في فروع مستقلة قبل دمجها في `staging`، ثم `main`.

---

## 🔄 سير عمل Git القياسي

### 1️⃣ **استنساخ المستودع**

لأول مرة:

```sh
git clone https://github.com/SafarAI-ProjectHub/safar-ai.git
cd safar-ai
```

للتأكد من أنك تعمل على الفرع الصحيح:

```sh
git checkout staging
```

---

### 2️⃣ **إنشاء فرع ميزة جديدة**

قبل بدء العمل على ميزة جديدة أو إصلاح مشكلة:

```sh
git checkout staging
git pull origin staging  # جلب أحدث التحديثات
git checkout -b feature-branch-name
```

اختر أسماء ذات معنى مثل:

- `feature-user-authentication`
- `fix-payment-gateway-bug`

---

### 3️⃣ **حفظ التعديلات (Commit)**

استخدم هذا التنسيق لرسائل الكوميت:

```sh
git add .
git commit -m "🔧 [Feature] Add user authentication"
git push origin feature-branch-name
```

- `🔧 [Feature]` لإضافة ميزة جديدة.
- `🐛 [Fix]` لإصلاح الأخطاء.
- `🚀 [Enhancement]` لتحسينات الكود.
- `📝 [Docs]` لتحديثات التوثيق.

---

### 4️⃣ **دمج الفرع مع Staging**

عند الانتهاء من الميزة:

```sh
git checkout staging
git pull origin staging
git merge feature-branch-name
git push origin staging
```

يتم إنشاء **Pull Request (PR)** لمراجعة الكود قبل الدمج في `main`.

---

### 5️⃣ **النشر إلى Main**

بعد الاختبار على `staging`، يتم الدمج إلى `main`:

```sh
git checkout main
git pull origin main
git merge staging
git push origin main
```

يتم تشغيل سكريبتات النشر تلقائيًا لتحديث بيئة الإنتاج.

---

### 6️⃣ **تحديث نسختك المحلية**

```sh
git checkout staging
git pull origin staging
git checkout main
git pull origin main
```

دائمًا تأكد من العمل بأحدث كود لتجنب التعارضات.

---

## 🛠️ أوامر Git المفيدة

| الأمر | الوصف |
|---------|------------|
| `git status` | عرض حالة التعديلات الحالية. |
| `git branch` | عرض جميع الفروع. |
| `git checkout branch-name` | التبديل إلى فرع آخر. |
| `git fetch origin` | جلب التحديثات من المستودع. |
| `git log --oneline` | عرض سجل الكوميتات بشكل مختصر. |

---

📌 **هذا الدليل ضروري للحفاظ على بيئة عمل منظمة وفعالة لمشروع SafarAI. يرجى الالتزام به لضمان تعاون سلس واحترافي.** 🚀

