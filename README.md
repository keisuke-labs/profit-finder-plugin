# profit-finder プラグイン

eBay Profit Finder の調査結果を、Claude Code / Cowork の会話の中で扱うためのプラグインです。
利益候補の一覧、出品判断の記録、メルカリの在庫・最安値の確認といった作業を、スキルと MCP 接続で行えます。

MCP サーバー（`pf`）は OAuth で保護されています。**招待済みの利用者だけが使えます。**
招待されていないアカウントでは、プラグインを入れても認証を通過できません。

## 導入方法

### Claude Code

1. marketplace を追加します。

   ```
   /plugin marketplace add keisuke-labs/profit-finder-plugin
   ```

2. プラグインをインストールします。

   ```
   /plugin install profit-finder@profit-finder
   ```

3. `/mcp` を開き、`plugin:profit-finder:pf` を選んで認証します。ブラウザが開くので、招待されたアカウントでサインインしてください。

### Cowork

1. Customize > Plugins > Add marketplace に `keisuke-labs/profit-finder-plugin` を入力して追加します。
2. 一覧から profit-finder をインストールします。
3. プラグインの Connectors タブで `pf` に接続し、OAuth でサインインします。

### 手動で MCP サーバーを追加済みの場合

すでに `claude mcp add … pf` で同じサーバーを追加している場合は、その設定がそのまま使われます。
同じ URL のサーバーは 1 つにまとめられ、手動で追加した定義が優先されるため、二重に接続されることはありません。

## スキル

次のスキルが入っています。

| スキル | 内容 |
|---|---|
| `pf-candidates` | 直近の調査から利益候補を一覧し、カードの詳細や run ごとの商品リストを見る |
| `pf-listing-check` | 候補を出品対象にする／見送る／見送りから戻す（書き込み前に確認） |
| `pf-soldout` | メルカリ候補の売り切れを付ける／外す（書き込み前に確認） |
| `pf-stock-check` | メルカリ候補がいまも買えるかを実ページで確かめ、売り切れは確認のうえ記録する |
| `pf-lowest-price` | メルカリと eBay のいまの最安値を実ページで調べる |

`pf-stock-check` と `pf-lowest-price` は Claude in Chrome で実ページを読むため、Claude in Chrome が使える環境が必要です。
