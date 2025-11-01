# دليل التعديل على موقع Bold Graphic Portfolio

هذا الدليل سيعلمك كيف تعدل على موقعك بنفسك دون الحاجة لمعرفة برمجية متقدمة.

---

## 1. تغيير الألوان (الأهم!)

جميع ألوان الموقع موجودة في **ملف واحد فقط**:

📁 **المسار:** `client/src/index.css`

### كيف تغير الألوان؟

افتح الملف `client/src/index.css` وابحث عن السطر 45 (`:root {`)

ستجد هذه الألوان:

```css
:root {
  /* Bold Graphic Color System: Black, Bold Blue (#3B82F6), White */
  --primary: var(--color-blue-500); /* اللون الأساسي (الأزرق) */
  --background: oklch(1 0 0); /* خلفية الموقع (أبيض) */
  --foreground: oklch(0 0 0); /* لون النص (أسود) */
  --secondary: oklch(0.1 0 0); /* اللون الثانوي (رمادي غامق) */
  --muted: oklch(0.96 0 0); /* لون خافت (رمادي فاتح) */
}
```

### لتطبيق ألوان هويتك (أزرق سماوي، أصفر، برتقالي):

**استبدل الأسطر من 46 إلى 79 بهذا الكود:**

```css
:root {
  /* Boldraphic Color System: Sky Blue, Lemon Yellow, Orange */
  --primary: oklch(0.7 0.15 220); /* أزرق سماوي */
  --secondary: oklch(0.85 0.12 100); /* أصفر ليموني */
  --accent: oklch(0.7 0.15 40); /* برتقالي */
  
  --background: oklch(0.98 0.01 100); /* خلفية فاتحة مع لمسة صفراء */
  --foreground: oklch(0.3 0.05 220); /* نص أزرق غامق */
  
  --primary-foreground: oklch(1 0 0); /* أبيض */
  --secondary-foreground: oklch(0.3 0.05 220); /* أزرق غامق */
  --accent-foreground: oklch(1 0 0); /* أبيض */
  
  --muted: oklch(0.95 0.02 220); /* رمادي مزرق فاتح */
  --muted-foreground: oklch(0.5 0.05 220); /* رمادي مزرق */
  
  --card: oklch(1 0 0);
  --card-foreground: oklch(0.3 0.05 220);
  --popover: oklch(1 0 0);
  --popover-foreground: oklch(0.3 0.05 220);
  
  --border: oklch(0.9 0.02 220);
  --input: oklch(0.9 0.02 220);
  --ring: oklch(0.7 0.15 220);
  
  --radius: 0.5rem; /* زوايا منحنية أكثر */
}
```

**احفظ الملف** وسترى التغييرات مباشرة في المتصفح!

---

## 2. تغيير الخط

الخط الحالي: **Poppins** (جريء ومستقيم)

### لتغيير الخط:

1. **افتح:** `client/index.html`
2. **ابحث عن السطر 15** (رابط Google Fonts)
3. **استبدل** `Poppins` باسم الخط الذي تريده

**مثال:** لو تريد خط **Nunito** (أكثر مرونة):

```html
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800;900&display=swap" rel="stylesheet" />
```

4. **افتح:** `client/src/index.css`
5. **ابحث عن السطر 124** وغير اسم الخط:

```css
body {
  font-family: 'Nunito', sans-serif; /* بدلاً من Poppins */
}
```

---

## 3. تعديل المحتوى النصي

### الصفحة الرئيسية:
📁 **الملف:** `client/src/pages/Home.tsx`

**لتغيير العنوان الرئيسي:**
```tsx
<h1 className="text-5xl md:text-7xl lg:text-8xl font-black tracking-tight leading-tight">
  تصاميم  {/* غير هذا النص */}
  <br />
  <span className="text-primary">جريئة</span> ومميزة  {/* وهذا */}
</h1>
```

**لتغيير الوصف:**
```tsx
<p className="text-lg md:text-xl text-muted-foreground max-w-2xl mx-auto leading-relaxed">
  أحول أفكارك إلى تصاميم بصرية قوية تترك أثراً. {/* غير هذا النص */}
</p>
```

**لتغيير الإحصائيات:**
```tsx
<div className="text-4xl font-black text-primary">50+</div>  {/* غير الرقم */}
<div className="text-sm text-muted-foreground">مشروع مكتمل</div>  {/* غير النص */}
```

---

### صفحة "من أنا":
📁 **الملف:** `client/src/pages/About.tsx`

**لتغيير قصتك:**
```tsx
<p>
  أنا مصمم جرافيك متخصص في الهوية البصرية...  {/* غير هذا النص */}
</p>
```

**لتغيير المهارات:**
```tsx
const skills = [
  "Adobe Photoshop",  // أضف أو احذف مهارات
  "Adobe Illustrator",
  // ... إلخ
];
```

---

### صفحة التواصل:
📁 **الملف:** `client/src/pages/Contact.tsx`

**لتغيير معلومات التواصل:**
```tsx
const contactInfo = [
  {
    icon: Mail,
    title: "البريد الإلكتروني",
    value: "contact@boldgraphic.com",  // غير البريد
    href: "mailto:contact@boldgraphic.com",
  },
  {
    icon: Phone,
    title: "الهاتف",
    value: "+966 XX XXX XXXX",  // غير رقم الهاتف
    href: "tel:+966XXXXXXXXX",
  },
  // ... إلخ
];
```

---

## 4. تغيير الشعار (Logo)

### في شريط التنقل:
📁 **الملف:** `client/src/components/Navbar.tsx`

**ابحث عن السطر 23:**
```tsx
<div className="text-2xl font-black tracking-tight cursor-pointer hover:text-primary transition-colors">
  BOLD<span className="text-primary">GRAPHIC</span>  {/* غير النص هنا */}
</div>
```

**غيره إلى:**
```tsx
<div className="text-2xl font-black tracking-tight cursor-pointer hover:text-primary transition-colors">
  BOLD<span className="text-primary">RAPHIC</span>  {/* أو أي نص تريده */}
</div>
```

**كرر نفس الخطوة في:**
- `client/src/components/Footer.tsx` (السطر 18)

---

## 5. إضافة/تعديل الأعمال (Portfolio)

📁 **الملف:** `client/src/pages/Portfolio.tsx`

**ابحث عن السطر 4** (`const portfolioItems`):

```tsx
const portfolioItems = [
  { 
    id: 1, 
    image: "/portfolio/اسم_الصورة.png",  // مسار الصورة
    title: "تصميم سوشيال ميديا",  // عنوان العمل
    category: "social"  // التصنيف
  },
  // أضف المزيد هنا...
];
```

### لإضافة عمل جديد:

1. **ارفع الصورة** إلى مجلد: `client/public/portfolio/`
2. **أضف عنصر جديد** في `portfolioItems`:

```tsx
{ 
  id: 25,  // رقم تسلسلي جديد
  image: "/portfolio/my-new-work.png", 
  title: "تصميم جديد", 
  category: "branding" 
},
```

---

## 6. تغيير روابط التواصل الاجتماعي

📁 **الملف:** `client/src/components/Footer.tsx`

**ابحث عن السطر 6:**
```tsx
const socialLinks = [
  { icon: Instagram, href: "#", label: "Instagram" },  // غير # برابط حسابك
  { icon: Twitter, href: "#", label: "Twitter" },
  { icon: Linkedin, href: "#", label: "LinkedIn" },
  { icon: Mail, href: "mailto:contact@boldgraphic.com", label: "Email" },
];
```

**مثال:**
```tsx
{ icon: Instagram, href: "https://instagram.com/boldraphic", label: "Instagram" },
```

---

## 7. كيف تشوف التغييرات؟

بعد أي تعديل:
1. **احفظ الملف** (Ctrl+S أو Cmd+S)
2. **ارجع للمتصفح** - التغييرات ستظهر تلقائياً!

---

## 8. نصائح مهمة

✅ **اعمل نسخة احتياطية** قبل أي تعديل كبير
✅ **غير شيء واحد في المرة** عشان تعرف إذا صار خطأ
✅ **استخدم محرر نصوص** مثل VS Code أو Cursor
✅ **لو صار خطأ:** ارجع للنسخة السابقة من الملف

---

## هل تحتاج مساعدة؟

إذا واجهتك أي مشكلة أثناء التعديل، فقط أخبرني وسأساعدك!
