# 🧠 clarify-and-learn

<div align="center">

**Claude Code skill — önce projeyi anla, sonra kod yaz.**

![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet?style=for-the-badge&logo=anthropic)
![Language](https://img.shields.io/badge/Dil-Türkçe-red?style=for-the-badge)
![License](https://img.shields.io/badge/Lisans-MIT-green?style=for-the-badge)

</div>

---

## 🎯 Ne Sorun Çözüyor?

Çoğu geliştirici Claude'a bir şey söyler, Claude da anında koda dalar. Belirsizlik varsa ya yanlış bir şey yazar, ya da anlamsız sorular sorar.

**Bu skill ikisini de engeller.**

```
❌ Olmadan:   "Bunu ekle" → Claude tahmin eder → Yanlış çıktı → Sen düzeltirsin

✅ Bununla:   "Bunu ekle" → Proje taranır → Net olmayan tek şey sorulur → Doğru çıktı
```

---

## ✨ Özellikler

### 1️⃣ Önce Tara, Sonra Sor

Claude soru sormadan önce **otomatik olarak projeyi inceler:**

```
📁 Dosya yapısı          → Hangi framework, hangi mimari?
📦 package.json / pyproject.toml  → Hangi kütüphaneler var?
🔍 İlgili dosyalar       → İstenilen özellik nerede etkili?
📝 Git log               → Son zamanlarda ne üzerinde çalışılmış?
```

> Tarama ile anlaşılabilecek hiçbir şey kullanıcıya sorulmaz.

---

### 2️⃣ Sadece Gerçekten Belirsiz Olanı Sorar

Tarama sonrası net olmayan sadece **iş kararları** sorulur. Maksimum 3 soru.

```
✅ Sorar:   "Bildirimler WebSocket mi yoksa polling mi olsun?"
✅ Sorar:   "Ücretsiz kullanıcı limiti kaç?"

❌ Sormaz:  "Hangi dosyada yapayım?"    → Bulur.
❌ Sormaz:  "React mı kullanıyorsunuz?" → Görür.
```

---

### 3️⃣ Öğrenme Modu 📚

`öğrenme` argümanı eklendiğinde Claude her değişikliği gerekçesiyle açıklar:

<table>
<tr>
<th>Normal Mod</th>
<th>Öğrenme Modu</th>
</tr>
<tr>
<td>

```ts
// auth.ts
const token = await signJWT(payload)
```

</td>
<td>

```ts
// auth.ts
const token = await signJWT(payload)
```

📚 **Neden böyle yaptım**
- **Dosya:Satır** — auth.ts:14
- **Neden** — JWT, stateless session sağlar;
  DB'ye her istekte sorgu atmayı önler
- **Referans** — `jsonwebtoken` / RFC 7519

</td>
</tr>
</table>

---

## 🔄 Akış Diyagramı

```
Kullanıcı isteği geldi
        │
        ▼
┌───────────────────┐
│  Projeyi Tara     │  ← package.json, dosya yapısı, git log, ilgili dosyalar
└────────┬──────────┘
         │
         ▼
  İstek net mi?
    /        \
  EVET        HAYIR
   │            │
   │      ┌─────────────┐
   │      │ Max 3 soru  │
   │      │ (sadece iş  │
   │      │  kararları) │
   │      └──────┬──────┘
   │             │
   └──────┬──────┘
          │
          ▼
   Öğrenme modu?
    /          \
  EVET          HAYIR
   │              │
   ▼              ▼
Açıklamalı     Direkt
  Kod          Çıktı
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

# Öğrenme modu — her adımı açıkla
/cl öğrenme kullanıcı profil sayfası yap
```

---

## 💬 Örnek Diyalog

```
Sen:    /cl dashboard'a bildirim sistemi ekle

Claude: Projeyi taradım:
        ✓ React + Zustand kullanılıyor
        ✓ Mevcut bir bildirim komponenti yok
        ✓ API'de /notifications endpoint var

        Netleştirmem gereken 1 nokta:

        1) Bildirimler nasıl güncellensin?
           a) WebSocket   → anlık, sunucu desteği gerekir
           b) Polling     → basit, 30 sn aralıkla kontrol

Sen:    b

Claude: [doğrudan koda geçer]
```

---

## 📁 Repo Yapısı

```
clarify_and_learn/
├── SKILL.md                    # Skill tanımı ve kurallar
├── .claude/
│   └── commands/
│       └── cl.md               # /cl kısayolu
└── README.md
```

---

## 📄 Lisans

MIT
