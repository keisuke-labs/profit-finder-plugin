# profit-finder-plugin

Claude Code / Cowork 用の profit-finder プラグインを配布する公開リポジトリです。

## version の更新

プラグインの中身（`plugins/profit-finder/` 配下のスキル・`.mcp.json` など）を変えたら、同じコミットで `plugins/profit-finder/.claude-plugin/plugin.json` の `version` を上げてください。
プラグインは version ごとにキャッシュされるため、version を上げないと利用者の環境で更新として扱われず、変更が届きません。

## 公開リポジトリとしての注意

秘密情報や、運用側の内部構成（サーバー側のインフラや元リポジトリのコードなど）は書かないでください。
