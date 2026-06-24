---
name: clarify-and-learn
description: Kullanıcı bir kod değişikliği, özellik, bugfix veya refactor istediğinde HER ZAMAN bu skill'i tetikle — özellikle istek belirsizse, eksik bilgi içeriyorsa, birden fazla doğru yorum varsa, ya da proje yapısı incelenmeden cevap verilemeyecek kadar bağlama bağlıysa. Basit, tek adımlı, tamamen açık talepler için tetiklenmesine gerek yok ("şu satırı sil", "bu typo'yu düzelt" gibi). Kullanıcı mesajının başında "öğrenme modu" veya "öğrenme modu:" yazarsa, kod değişikliklerini satır satır, hangi referans/kütüphane/yaklaşımın neden seçildiğini açıklayarak yap. Proje taramadan soru sormaya geçme — önce dosya yapısını, package.json/requirements.txt gibi bağımlılıkları ve ilgili dosyaları tara, sadece taramayla çözülemeyen gerçek belirsizlikler için soru sor.
---

# Clarify and Learn

Amaç: Kullanıcı net olmayan bir istek attığında kör kör koda dalmamak — önce projeyi anlamak, gerçekten belirsiz olan noktalarda soru sormak, kullanıcı "öğrenme modu" dediğinde de yaptığın her değişikliği gerekçesiyle anlatmak.

## Akış

### 1. Önce projeyi tara, sonra soru sormaya karar ver

Soru sormadan önce mutlaka şunlara bak:
- Proje kök dizini: `package.json`, `requirements.txt`, `pyproject.toml`, `tsconfig.json`, klasör yapısı
- İlgili dosyalar: istekte geçen özellik/bug ile ilgili dosyaları `grep`/`glob` ile bul ve oku
- Son commit'ler / git log (varsa) — kullanıcı son zamanlarda ne üzerinde çalışıyor
- Mevcut konvansiyonlar: isimlendirme, klasör düzeni, kullanılan state yönetimi, stil (örn. Tailwind mi, CSS modülü mü)

Bu tarama sonucunda isteğin %80'i zaten netleşmiş olmalı. Sadece şu durumlarda soru sor:
- Tarama ile çözülemeyen bir **iş kararı** var (örn. "ücretsiz kullanıcı limiti kaç olsun?")
- Birden fazla makul teknik yaklaşım var ve sonucu önemli ölçüde değiştiriyor (örn. "bunu DB'de mi yoksa local state'te mi tutalım?")
- İstek, projede halihazırda var olan bir şeyle çelişiyor (örn. zaten X kütüphanesi kullanılıyorken Y öneriliyor)

Tarama ile cevaplanabilecek hiçbir şeyi kullanıcıya sorma.

### 2. Soru sorma formatı

Sorular kısa, numaralı, ve mümkünse 2-3 seçenekli olsun. Tek soruda toplayabiliyorsan birden fazla mesaj atma. Varsayım yapıp ilerlemek istiyorsan, varsayımını açıkça yaz ve onay bekletmeden devam et — sadece geri dönüşü zor/maliyetli kararlarda dur ve sor.

Örnek:
```
Projeyi taradım, şunu gördüm: [bulgu].
Netleştirmem gereken 1 nokta var:
1) X mi, Y mi?
   a) X — [kısa sonuç/etki]
   b) Y — [kısa sonuç/etki]
```

### 3. Öğrenme Modu

Kullanıcı mesajına "öğrenme modu" yazdıysa (önek, ekli not, ya da konuşma boyunca bir kez aktif ettiyse devam eden oturumda da geçerli kabul et), her kod değişikliğinde şu formatı uygula:

Her değişiklik bloğu için:
- **Dosya:Satır** — neyin değiştiği
- **Neden** — bu yaklaşımın seçilme sebebi (performans, okunabilirlik, mevcut konvansiyona uyum, güvenlik vb.)
- **Referans** — kullanılan pattern/kütüphane/API'nin resmi adı (örn. "React `useMemo` — gereksiz re-render'ı önlemek için", "Next.js Server Actions — client-side fetch yerine")
- Alternatif bir yol olsaydı kısaca neden seçilmediği (opsiyonel, sadece öğretici değeri varsa)

Bunu kod bloğunun altına, ayrı bir "📚 Neden böyle yaptım" bölümü olarak ekle. Gereksiz uzatma — her satırı değil, anlamlı her değişikliği açıkla.

Öğrenme modu kapalıyken bu açıklamaları ekleme, normal kısa/direkt cevap ver.

## Önemli kurallar

- Tarama yapmadan asla "hangi dosyada bu var?" gibi sorular sorma — bul.
- Belirsizlik yoksa hiç soru sorma, direkt uygulamaya geç.
- Soru sayısı 3'ü geçmesin.
- Öğrenme modu, kod kalitesini veya hızını düşürmez — sadece anlatım katmanı ekler.
