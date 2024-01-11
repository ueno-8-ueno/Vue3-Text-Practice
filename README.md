# Vue3-Text-Practice
"Vue3 フロントエンド開発の教科書" での学習記録用リポジトリ

# セットアップメモ
- **node v20.11.0**

### プロジェクト作成
```bash
npm init vue@latest
```
|質問|回答|
|:---|:---:|
|Project name|chapter${章番号}|
|Add TypeScript?|**Yes**|
|Add JSX Support?|No|
|Add Vue Router for Single Page Application development?|No(10章以降は**Yes**)|
|Add Pinia for state management?|No(11章以降は**Yes**)|
|Add Vitest for Unit Testing?|No(13章以降は**Yes**)|
|Add an End-to-End Testing Solution?|No|
|Add ESLint for code quality?|No|
|Add Prettier for code formatting?|No|

### パッケージのインストール
```bash
npm install
```

### サーバ起動
```bash
cd ${プロジェクトディレクトリ}
npm run dev
```
アクセス: http://localhost:5173/