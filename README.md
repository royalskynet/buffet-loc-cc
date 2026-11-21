# buffet 個人網站

使用繁體中文的個人開發筆記與開源專案網站，包含首頁、筆記與專案列表。
網站使用純 HTML／CSS，不需要安裝套件或執行建置。

## 本機預覽

在儲存庫根目錄執行：

```sh
python3 -m http.server 8080 --bind 127.0.0.1
```

開啟 <http://127.0.0.1:8080/>。頁面使用 `/style.css`、`/notes/` 等根目錄路徑，
請透過 HTTP 伺服器預覽，不要直接以 `file://` 開啟。

## 部署

透過 GitHub Pages 發布：在儲存庫 Settings → Pages 選擇從分支部署，
來源設為 `main` 分支的 `/ (root)`。推送至 `main` 後由 Pages 更新網站。

`CNAME` 記錄自訂網域 `www.buffet.loc.cc`；Pages 的 Custom domain 與 DNS
也必須指向此網站，並在憑證就緒後啟用 Enforce HTTPS。
變更網域時請同步更新 `CNAME`、Pages 設定與 DNS。
目前的根目錄連結適用於自訂網域，不適合直接部署在專案子路徑。

## 檢查

CI 會啟動本機伺服器，確認首頁、筆記、專案及樣式表可讀取，並以
[lychee](https://github.com/lycheeverse/lychee) 離線檢查 HTML 的內部連結與資源。
已安裝 lychee 時，可在根目錄執行：

```sh
lychee --offline --root-dir "$PWD" --index-files index.html './**/*.html'
```

離線模式不檢查外部網站是否可連線。
