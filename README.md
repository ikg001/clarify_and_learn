# clarify-and-learn

Claude Code skill — kör kör koda dalmadan önce projeyi tara, sadece gerçekten belirsiz noktalarda sor.

## Kurulum

```bash
git clone https://github.com/ikg001/clarify_and_learn.git
cp clarify_and_learn/SKILL.md ~/.claude/skills/clarify-and-learn/SKILL.md

# /cl kısayolu için
cp clarify_and_learn/.claude/commands/cl.md ~/.claude/commands/cl.md
```

## Kullanım

```
/clarify-and-learn <istek>
/cl <istek>
/cl öğrenme <istek>   # her değişikliği gerekçesiyle açıklar
```

## Davranış

- Soru sormadan önce projeyi tarar (`package.json`, bağımlılıklar, ilgili dosyalar)
- Yalnızca taramayla çözülemeyen noktalarda soru sorar (max 3)
- `öğrenme` argümanıyla: her değişiklik için dosya/satır + neden + hangi pattern

## Lisans

MIT
