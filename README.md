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

> AI ile kod yazıyorsun ama hiçbir şey öğrenmiyorsun. 6 ay sonra kendi kodunu açıklayamıyorsun.
> `öğrenme` argümanı bunu önler.

---

#### 🎬 Sahne 1 — Klasik AI Kodlama

```
 🧑‍💻  "Auth sistemi yaz"

 🤖  [Kod gelir]

     ┌─────────────────────────────────────┐
     │  const token = await signJWT(...)   │
     │  await redis.set(key, token, 3600)  │
     │  return { token, refreshToken }     │
     └─────────────────────────────────────┘

 🧑‍💻  "Çalışıyor, süper!"
      [kodu commit'ler, bir sonraki özelliğe geçer]
```

---

#### 🎬 Sahne 2 — 6 Ay Sonra

```
 👨‍💼  "Bu auth sistemini anlatır mısın?"

 🧑‍💻  "Yani... JWT kullanıyor."

 👨‍💼  "Neden Redis'e yazıyor?"

 🧑‍💻  "Hm... token expire için mi?"

 👨‍💼  "refreshToken ne zaman kullanılıyor?"

 🧑‍💻  "..."

 👨‍💼  "Bunu sen mi yazdın?"

 🧑‍💻  "Claude yazdı."

 👨‍💼  "Peki sen ne yaptın?"

 🧑‍💻  "..."

 ─────────────────────────────────────────
  AI kullandın ama hiçbir şey öğrenmedin.
  Kendi koduna yabancısın.
 ─────────────────────────────────────────
```

---

#### ✅ Öğrenme Moduyla Aynı Kod

```
 🧑‍💻  "/cl öğrenme auth sistemi yaz"
```

```ts
const token = await signJWT(payload)
await redis.set(`session:${userId}`, token, 3600)
return { token, refreshToken }
```

```
 ┌──────────────────────────────────────────────────────┐
 │  📚 Neden böyle yaptım                               │
 ├──────────────────────────────────────────────────────┤
 │                                                      │
 │  auth.ts:12 — signJWT                                │
 │  ✦ Neden: Stateless token; her istekte DB'ye         │
 │    sorgu atmadan doğrulama yapılır                   │
 │  ✦ Referans: RFC 7519 (JWT standartı)                │
 │  ✦ Alternatif: Session cookie → sunucu state'i       │
 │    gerektirir, horizontal scale'de sorun çıkarır     │
 │                                                      │
 │  auth.ts:13 — redis.set(..., 3600)                   │
 │  ✦ Neden: Logout = token blacklist; JWT kendi        │
 │    başına iptal edilemez, Redis bunu çözer           │
 │  ✦ 3600 sn = access token ömrü (güvenlik dengesi)   │
 │                                                      │
 │  auth.ts:14 — refreshToken                           │
 │  ✦ Neden: Access token kısa ömürlü tutulur;          │
 │    kullanıcı her 1 saatte login olmak zorunda        │
 │    kalmaz, refresh token sessioni uzatır             │
 └──────────────────────────────────────────────────────┘
```

---

#### 📈 Zamanla Fark

```
         Bilgi birikimi
              │
   Yüksek ████│                        ░░░░░░░░ Öğrenme Modu
              │                   ░░░░░
              │              ░░░░░
              │         ░░░░░
              │    ░░░░░
   Düşük  ────┼────────────────────────────────────────────
              │    ████████████████████████ Normal Mod
              │
              └──────────────────────────────────────────►
            Başlangıç        3 ay         6 ay       Zaman

  Normal mod: kod birikiyor, bilgi birikmiyor.
  Öğrenme modu: ikisi birlikte büyüyor.
```

---

#### ⚡ Karşılaştırma

<table>
<tr>
<th>Normal Mod</th>
<th>📚 Öğrenme Modu</th>
</tr>
<tr>
<td>

```ts
const token = await signJWT(payload)
await redis.set(key, token, 3600)
```
Bitti.

</td>
<td>

```ts
const token = await signJWT(payload)
await redis.set(key, token, 3600)
```

**📚 Neden böyle yaptım**
- Neden JWT: stateless, DB sorgusu yok
- Neden Redis: token iptal mekanizması
- 3600: access token ömrü, kasıtlı kısa
- Alternatif ve neden seçilmedi

</td>
</tr>
<tr>
<td>6 ay sonra: "bunu kim yazdı?"</td>
<td>6 ay sonra: her satırı açıklayabilirsin</td>
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
