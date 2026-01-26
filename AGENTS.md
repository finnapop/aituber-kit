# Repository Guidelines

## 繁體中文

### 專案結構與模組組織
- `src/` 為主要程式碼：`components/`、`features/`、`pages/`、`hooks/`、`lib/`、`utils/`、`styles/`、`types/`。
- 測試在 `src/__tests__/`，模擬（mock）在 `src/__mocks__/`。
- 靜態資源在 `public/`，文件在 `docs/`，本地化在 `locales/`。

### 建置、測試與開發指令
- `npm run dev`：啟動開發伺服器 `http://localhost:3000`。
- `npm run dev-https`：HTTPS 開發模式。
- `npm run build`：正式環境建置。
- `npm run start`：建置並啟動正式環境伺服器。
- `npm run desktop`：Electron 執行（需開發伺服器）。
- `npm run lint` / `npm run lint:fix`：ESLint 檢查/自動修復。
- `npm run format`：Prettier 格式化。
- `npm test` / `npm run test:watch` / `npm run test:coverage`：執行 Jest 測試。

### 程式風格與命名
- 以 TypeScript 為主，保持 strict 模式相容。
- Prettier 規則：`singleQuote: true`、不加分號。
- ESLint 使用 `next/core-web-vitals` + Prettier。
- 命名：React 元件 PascalCase，工具函式 camelCase，測試檔名 `*.test.ts(x)` 放在 `__tests__/`。

### 測試指南
- Jest + React Testing Library，`jest-environment-jsdom`。
- 修改核心邏輯時建議執行 `npm run test:coverage`。

### 提交與 PR 規範
- 提交訊息前綴常見：`feat:`、`fix:`、`chore(i18n):`，保持風格一致。
- PR（合併請求）聚焦單一變更，說明目的與影響。
- 目標分支為 `develop`。
- 介面變更請附截圖或短影片。

### 部署注意事項
- 完整功能需要 Node.js 主機（Next.js server + API routes）。
- GitHub Pages 僅靜態：`BASE_PATH=/你的倉庫名 npm run export` 發布 `out/`，API/即時功能/私密變數不可用。
- `BASE_PATH` 控制 `basePath` 與 `assetPrefix`。

### GitHub Pages（作品集）安全模式
- 僅作靜態展示，避免啟用需要伺服器或私密金鑰的功能（LLM/TTS/Realtime 等）。
- 不提交任何機密檔案（`.env`、`credentials.json`），也不要把金鑰寫進 `NEXT_PUBLIC_*`。
- 若要互動示範，請讓使用者自行輸入金鑰，並避免持久化或寫回儲存庫。

### 設定與安全
- 複製 `.env.example` 為 `.env`，不要提交 `.env`。
- 新增設定時同步更新 `.env.example`。
- `NEXT_PUBLIC_*` 會被打包到前端，視為公開資訊。
- 前端可見的變數皆視為公開，部署前參考 `README.md` 的安全說明。

### API 安全
- 優先使用伺服器端代理（Next.js API routes 或獨立後端），避免前端直接呼叫需要金鑰的服務。
- 金鑰只放在伺服器端環境變數或密鑰管理中，避免出現在日誌或錯誤訊息。
- 公開示範請採使用者自帶金鑰，僅短暫記憶體保存，不持久化。
- 建議加入來源限制/速率限制與輸入驗證，降低濫用風險。

### 本地化
- 僅更新 `locales/ja/`，其他語言由獨立流程管理。

## 日本語

### プロジェクト構成とモジュール
- `src/` に主要コード（`components/`、`features/`、`pages/`、`hooks/`、`lib/`、`utils/`、`styles/`、`types/`）。
- テストは `src/__tests__/`、モックは `src/__mocks__/`。
- 静的アセットは `public/`、ドキュメントは `docs/`、ローカライズは `locales/`。

### ビルド・テスト・開発コマンド
- `npm run dev`：開発サーバー起動（`http://localhost:3000`）。
- `npm run dev-https`：HTTPS で開発起動。
- `npm run build`：本番ビルド。
- `npm run start`：ビルドして本番起動。
- `npm run desktop`：Electron 実行（dev server が必要）。
- `npm run lint` / `npm run lint:fix`：ESLint 実行/修正。
- `npm run format`：Prettier 実行。
- `npm test` / `npm run test:watch` / `npm run test:coverage`：Jest 実行。

### コーディングスタイルと命名
- TypeScript を使用し、strict モード互換を保つ。
- Prettier ルール：`singleQuote: true`、セミコロンなし。
- ESLint は `next/core-web-vitals` + Prettier。
- 命名：React コンポーネントは PascalCase、ユーティリティは camelCase、テストは `*.test.ts(x)` を `__tests__/` に配置。

### テストガイドライン
- Jest + React Testing Library、`jest-environment-jsdom`。
- 主要ロジック変更時は `npm run test:coverage` 推奨。

### コミット & PR ガイド
- 例：`feat:`、`fix:`、`chore(i18n):` の短い接頭辞を踏襲。
- PR は 1 つの変更に集中し、目的と影響を説明。
- ターゲットブランチは `develop`。
- UI 変更はスクリーンショット/短い動画を添付。

### デプロイ注意事項
- フル機能には Node.js ホスト（Next.js server + API routes）が必要。
- GitHub Pages は静的のみ：`BASE_PATH=/リポジトリ名 npm run export` で `out/` 公開。API/リアルタイム/機密変数は不可。
- `BASE_PATH` が `basePath` と `assetPrefix` を制御。

### GitHub Pages（ポートフォリオ）安全モード
- 静的表示のみ。サーバーや秘密鍵が必要な機能（LLM/TTS/Realtime 等）は有効化しない。
- `.env` や `credentials.json` などの機密ファイルはコミットしない。`NEXT_PUBLIC_*` にキーを書かない。
- デモを行うなら利用者自身がキー入力する方式にし、永続化やリポジトリ保存は避ける。

### 設定とセキュリティ
- `.env.example` を `.env` にコピーし、`.env` はコミットしない。
- 設定追加時は `.env.example` も更新。
- `NEXT_PUBLIC_*` はビルド後にフロントへ埋め込まれるため公開情報として扱う。
- フロントから見える変数は公開扱い。配備前に `README.md` の注意事項を確認。

### API セキュリティ
- 可能ならサーバー側プロキシ（Next.js API routes または外部バックエンド）経由にし、フロントから秘密鍵を使わない。
- 鍵はサーバーの環境変数/シークレットに保存し、ログやエラーに出力しない。
- 公開デモは利用者のキー入力方式にし、メモリ保持のみで永続化しない。
- オリジン制限/レート制限と入力検証を行い、濫用を抑える。

### ローカライズ
- 更新は `locales/ja/` のみ。その他は別プロセスで管理。
