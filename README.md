# Bloc Recruitment Alerts

CK3 Bloc勧誘・引き抜き通知Mod

家系陣営（Bloc/Confederation）の指導者としてプレイ中、勧誘可能かつ実際に加入してくれそうな家を自動検知し、警告枠で通知します。

本リポジトリは [jesec/ck3-mod-base](https://github.com/jesec/ck3-mod-base) をforkし、CK3本体ファイルをgit管理下に置く構成を採用しています。

## 構成

- `base/game/` — CK3本体ファイル（バニラ）。git管理下にあり、本体アップデート追従はgit mergeで行う
- `mod/` — 本Modの独自ファイル（判定ロジック・月次スキャン・警告枠・表示文）。常に`base/`より優先される
- `out/` — ビルド出力（gitignore対象）
- `build.sh` / `install.sh` — ビルド・インストールスクリプト（詳細は[base/docs/repo.md](base/docs/repo.md)を参照）

## 開発

現状、本Modは`base/game/`内のファイルを直接編集していないため（全て`mod/`配下の新規ファイル）、`out/`と`mod/`の中身は常に一致します。通常の開発では`build.sh`を都度実行する必要はなく、CK3のModポインタを`mod/`に直接向けて動作確認できます。

`base/game/`側のファイルを直接編集する変更を行う場合は、`bash build.sh`でビルドしてから確認してください。

## 本体アップデート時

```bash
git fetch ck3-base-upstream --tags
git merge base/<新バージョン>
bash build.sh
```
