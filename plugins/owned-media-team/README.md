# owned-media-team

オウンドメディアをAIチームで運用するためのCoworkプラグイン。6つの担当(ロール)がそれぞれスキルとして独立し、**編集カレンダーを唯一の進行表**として日次で分担実行する。

## 含まれるスキル

| スキル | ロール | 起動例 |
|---|---|---|
| `om-standup` | 進行(デスク) | 「今日のオウンドメディア」「朝会」 |
| `om-editor` | 編集長・企画 | 「今週の企画」「記事を承認して」「月次KPI」 |
| `om-research` | リサーチ担当 | 「この記事のリサーチして」 |
| `om-writer` | ライター・編集 | 「記事を書いて」「原稿を整えて」 |
| `om-llmo` | SEO/LLMO担当 | 「公開前チェック」「AI露出を定点観測」 |
| `om-distribute` | メディア更新担当 | 「SNS展開案を作って」 |

## 前提

- 同プロジェクトの **review-research** スキル(顧客の声の収集)と **aio-check** スキル(AI露出・LLMO診断)を部品として使う
- 共有状態はプロジェクトドキュメントの `claude/owned-media/` 配下に置く
- 運用規約の全文は `claude/owned-media/設計書.md`

## 導入手順

1. このプラグインをCoworkに追加する
2. **体制設計書を `claude/owned-media/設計書.md` としてプロジェクトに保存する**(全スキルがここを共通規約として参照するため、無いと参照が空振りする)
3. `assets/brands.template.json` をもとに `claude/owned-media/brands.json` を作る(ブランド名・URL・カテゴリ・著者/監修者・競合・週の本数)
4. `assets/calendar.template.json` を `claude/owned-media/calendar.json` として置く
5. 「今週の企画」で編集長を起動し、カレンダーに記事を積む
6. 日次スケジュールタスクを登録して自動運転を開始する

## 設計上の約束

- 外部公開(CMS投稿・SNS投稿)はAIが実行しない。案の作成までで、実行は人の承認後
- 計測できない値は捏造せず「取得できず/未計測」と書く
- statusを `ready` と `done` に進められるのは編集長ロールだけ
