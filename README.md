# 🧠 clarify-and-learn

<div align="center">

**Claude Code skill — önce projeyi anla, sonra kod yaz.**

![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet?style=for-the-badge&logo=anthropic)
![Language](https://img.shields.io/badge/Dil-Türkçe-red?style=for-the-badge)
![License](https://img.shields.io/badge/Lisans-MIT-green?style=for-the-badge)

</div>

---

## 💀 Vibe Coding Tuzağı

> **Vibe coding** = AI'ya bir şeyler söyleyip, ne yazdığını anlamadan "çalışıyor, tamam" diye ilerlemek.

Başta harika görünür. Sonra production yanar.

---

### 🎬 Sahne 1 — Mutlu Başlangıç

```
 Pazartesi sabahı, kahve elinde, hevesle:
 ┌─────────────────────────────────────────────────────┐
 │                                                     │
 │  🧑‍💻  "Şu ödeme sayfasını yenile, daha modern olsun" │
 │                                                     │
 │  🤖  [Claude 400 satır kod yazar]                   │
 │                                                     │
 │  🧑‍💻  "Vay be, harika görünüyor!"                    │
 │       deploy 🚀                                     │
 │                                                     │
 └─────────────────────────────────────────────────────┘
```

---

### 🎬 Sahne 2 — Sessiz Tehlike

```
 Aynı gün, arka planda:

   Kullanıcı ödeme yapıyor...
        │
        ▼
   ┌──────────────────────────────────────┐
   │  form.submit()                       │
   │    → validation.js ← Claude burayı  │
   │         değiştirmedi sanıyordu       │
   │    → payment_handler.php ← ama bu   │
   │         eski kodu bekliyor          │
   │    → ??? ← kimse bilmiyor           │
   └──────────────────────────────────────┘
        │
        ▼
   Hata yok. Sessizce kırık.
   Siparişler düşüyor. Kimse fark etmiyor.
```

---

### 🎬 Sahne 3 — Felaket

```
 ┌─────────────────────────────────────────────────────┐
 │                                                     │
 │  📱 Saat 03:00 — Telefon çalıyor                    │
 │                                                     │
 │  😱 "Ödeme sistemi çalışmıyor, 6 saattir!"          │
 │                                                     │
 │  🧑‍💻  kodu açar...                                   │
 │                                                     │
 │       payment_handler.php:47                        │
 │       ❓ Bu ne?                                      │
 │       ❓ Bunu kim yazdı?                             │
 │       ❓ Neden böyle?                                │
 │                                                     │
 │  🤖  "Siz istediniz, ben yazdım."                   │
 │  🧑‍💻  "Ama ben ne istediğimi bilmiyordum ki!"        │
 │                                                     │
 └─────────────────────────────────────────────────────┘

  Vibe coding'in faturası production'da ödenir.
```

---

### ✅ Bu Skill Nasıl Çözer?

```
  SEN                 clarify-and-learn        PRODUCTION
   │                        │                      │
   │  "ödeme sayfasını      │                      │
   │   yenile"              │                      │
   │ ─────────────────────► │                      │
   │                        │                      │
   │                   📂 Proje taranır            │
   │                   payment_handler.php görülür │
   │                   validation.js bağlantısı    │
   │                   anlaşılır                   │
   │                        │                      │
   │  ◄─────────────────────│                      │
   │  "validation eski API  │                      │
   │   bekliyor, yeni form  │                      │
   │   bunu kırar. Uyumu    │                      │
   │   koruyayım mı?"       │                      │
   │                        │                      │
   │  "evet"                │                      │
   │ ─────────────────────► │                      │
   │                        │ doğru, güvenli kod   │
   │                        │ ───────────────────► │
   │                        │                      │
   │                        │               ✅ Çalışır
   │                        │               03:00'de kimse
   │                        │               aramaz
```

---

### 📊 Fark Ne?

```
╔══════════════════════════════════════════════════════════╗
║            ❌ VİBE CODİNG          ✅ BU SKİLL           ║
╠══════════════════════════════════════════════════════════╣
║  Claude tahmin eder          Proje önce taranır          ║
║  Sen "çalışıyor" dersin      Belirsizlik önceden çözülür ║
║  Gizli bağımlılıklar kırılır Bağlantılar görülür         ║
║  Production'da patlak        İlk seferinde doğru         ║
║  Gece 03:00 krizi            Sağlıklı uyku               ║
╚══════════════════════════════════════════════════════════╝
```

---

## ✨ Özellikler

### 1️⃣ Önce Tara, Sonra Sor

Claude soru sormadan önce **otomatik olarak projeyi inceler:**

```
 ┌─────────────────────────────────────────────┐
 │  🔍 OTOMATIK PROJE TARAMASI                 │
 ├─────────────────────────────────────────────┤
 │  📁  Dosya yapısı    →  Mimari & framework  │
 │  📦  Bağımlılıklar   →  Hangi kütüphaneler  │
 │  🔎  İlgili dosyalar →  Nerede değişecek    │
 │  📝  Git log         →  Son çalışmalar      │
 └─────────────────────────────────────────────┘
```

> Tarama ile anlaşılabilecek hiçbir şey kullanıcıya sorulmaz.

---

### 2️⃣ Sadece Gerçekten Belirsiz Olanı Sorar

```
╔══════════════════════════════════════════════╗
║  SORAR ✅           SORMAZ ❌                ║
╠══════════════════════════════════════════════╣
║  "WebSocket mı,     "Hangi dosyada           ║
║   polling mi?"       yapayım?"  → Bulur.     ║
║                                              ║
║  "Limit kaç         "React mı               ║
║   olsun?"            kullanıyorsun?" → Görür ║
╚══════════════════════════════════════════════╝
  Max 3 soru. Tarama ile çözülebilecek
  hiçbir şey sorulmaz.
```

---

### 3️⃣ Öğrenme Modu 📚

`öğrenme` argümanı eklendiğinde Claude her değişikliği gerekçesiyle açıklar:

<table>
<tr>
<th>⚡ Normal Mod</th>
<th>📚 Öğrenme Modu</th>
</tr>
<tr>
<td>

```ts
const token = await signJWT(payload)
```
Bitti.

</td>
<td>

```ts
const token = await signJWT(payload)
```

**📚 Neden böyle yaptım**
- `auth.ts:14` — JWT oluşturma
- **Neden:** Stateless session; her
  istekte DB sorgusu atmayı önler
- **Referans:** `jsonwebtoken` / RFC 7519
- **Alternatif:** Session cookie —
  sunucu state'i gerektirir, seçmedik

</td>
</tr>
</table>

---

## 🔄 Nasıl Çalışır?

```
        SEN BİR İSTEK ATIYORSUN
                  │
                  ▼
    ┌─────────────────────────┐
    │   📂 Proje Taranıyor   │
    │   ▓▓▓▓▓▓▓▓▓▓▓ 100%    │
    └────────────┬────────────┘
                 │
        ┌────────▼────────┐
        │   Net mi?       │
        └──┬──────────┬───┘
           │          │
          EVET       HAYIR
           │          │
           │    ┌─────▼──────────┐
           │    │ 🙋 Max 3 soru  │
           │    │ (sadece iş     │
           │    │  kararları)    │
           │    └─────┬──────────┘
           │          │
           └────┬─────┘
                │
       ┌────────▼────────┐
       │  Öğrenme modu?  │
       └──┬──────────┬───┘
          │          │
         EVET       HAYIR
          │          │
    ┌─────▼──┐  ┌────▼─────┐
    │ Kodla  │  │  Kodla   │
    │   +    │  │  direkt  │
    │ Açıkla │  └──────────┘
    └────────┘
```

---

## 💬 Gerçek Hayat Örneği

```
╔══════════════════════════════════════════════════════╗
║  SEN                                                 ║
║  /cl dashboard'a bildirim sistemi ekle               ║
╠══════════════════════════════════════════════════════╣
║  CLAUDE                                              ║
║  Projeyi taradım:                                    ║
║    ✓ React + Zustand → state yönetimi belli          ║
║    ✓ /notifications endpoint var → API hazır         ║
║    ✗ Notification komponenti yok → sıfırdan yazacak  ║
║                                                      ║
║  1 nokta net değil:                                  ║
║  Bildirimler nasıl güncellensin?                     ║
║    a) WebSocket  → anlık, sunucu desteği gerekir     ║
║    b) Polling    → basit, 30 sn aralıkla             ║
╠══════════════════════════════════════════════════════╣
║  SEN                                                 ║
║  b                                                   ║
╠══════════════════════════════════════════════════════╣
║  CLAUDE                                              ║
║  [doğrudan koda geçer — ilk seferinde doğru]         ║
╚══════════════════════════════════════════════════════╝
```

---

## 📦 Kurulum

**1. Repoyu klonla:**

```bash
git clone https://github.com/ikg001/clarify_and_learn.git
```

**2. Skill dosyasını yerleştir:**

```bash
mkdir -p ~/.claude/skills/clarify-and-learn
cp clarify_and_learn/SKILL.md ~/.claude/skills/clarify-and-learn/SKILL.md
```

**3. `/cl` kısayolunu ekle:**

```bash
mkdir -p ~/.claude/commands
cp clarify_and_learn/.claude/commands/cl.md ~/.claude/commands/cl.md
```

---

## 🚀 Kullanım

```bash
# Tam skill adıyla
/clarify-and-learn kullanıcı profil sayfası yap

# Kısayol ile
/cl kullanıcı profil sayfası yap

# Öğrenme modu — her adımı gerekçesiyle açıkla
/cl öğrenme kullanıcı profil sayfası yap
```

---

## 📁 Repo Yapısı

```
clarify_and_learn/
├── SKILL.md                 # Skill tanımı ve akış kuralları
├── .claude/
│   └── commands/
│       └── cl.md            # /cl kısayolu
└── README.md
```

---

## 📄 Lisans

MIT
