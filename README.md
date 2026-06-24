# clarify-and-learn — Claude Code Skill

> Kör kör koda dalmadan önce projeyi anla, gerçekten belirsiz noktalarda sor, öğrenme modunda her adımı açıkla.

## Ne yapar?

Bu skill, Claude Code'a iki davranış kazandırır:

**1. Akıllı Soru Sorma**
Belirsiz bir istek geldiğinde önce projeyi tarar (`package.json`, bağımlılıklar, ilgili dosyalar, git log), sonra **yalnızca taramayla çözülemeyen** noktalarda soru sorar. Taramayla anlaşılabilecek hiçbir şeyi kullanıcıya sormaz.

**2. Öğrenme Modu**
Mesajın başına `öğrenme modu:` eklenirse Claude her değişikliği gerekçesiyle açıklar:
- Hangi dosya, hangi satır
- Neden bu yaklaşım seçildi
- Hangi pattern/kütüphane/API kullanıldı

## Kurulum

### 1. Skill dosyasını indir

```bash
# ~/.claude/skills/ klasörüne kopyala
mkdir -p ~/.claude/skills/clarify-and-learn
```

`SKILL.md` dosyasını `~/.claude/skills/clarify-and-learn/SKILL.md` olarak kaydet.

### 2. Kısayol dosyasını ekle (opsiyonel)

`cl.md` dosyasını `~/.claude/skills/cl.md` olarak kaydet.

Bu sayede `/cl` komutuyla skill'i hızla tetikleyebilirsin.

## Kullanım

```
# Standart kullanım (belirsiz isteğin başında otomatik tetiklenir)
/clarify-and-learn

# Kısayol ile
/cl bir login sayfası yap

# Öğrenme modu — her değişikliği açıkla
/cl öğrenme bir login sayfası yap
```

## Örnek akış

```
Sen:   /cl kullanıcı dashboarduna bildirim sistemi ekle

Claude: Projeyi taradım:
        - React + Zustand kullanılıyor
        - Mevcut bir notification komponenti yok
        - API'de /notifications endpoint var

        Netleştirmem gereken 1 nokta:
        1) Bildirimler real-time mi (WebSocket) yoksa polling mi?
           a) WebSocket — anlık, ama sunucu desteği gerekir
           b) Polling — basit, 30 sn aralıkla kontrol
```

## Dosyalar

| Dosya | Açıklama |
|-------|----------|
| `SKILL.md` | Skill'in tam tanımı ve akış kuralları |
| `cl.md` | `/cl` kısayolu — skill'i hızla çağırır |

## Lisans

MIT
