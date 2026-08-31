# 就活ノート（配信版）

自宅PCが起動していなくてもスマホから読めるようにするための配信先。

```
PC(notes-viewer) --暗号化--> このリポジトリ --GitHub Pages--> スマホ(パスフレーズで復号)
```

置いてあるのは **AES-GCM で暗号化した暗号文だけ** で、
パスフレーズを知らないと中身は読めません（鍵はここには入っていません）。

## 更新のしかた

PC側で:

```
python C:\Users\kawau\notes-viewer\publish_encrypted.py
```

md → HTML 変換 → 暗号化 → push まで一度に走ります。

## 復号の条件

- PBKDF2-HMAC-SHA256 / 310,000回 / salt はビルドごとに更新
- AES-256-GCM（IVはファイルごと）
- スマホ側はパスフレーズだけを localStorage に持ちます
