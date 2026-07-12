# 買取 銭ちゃん（SEN CHAN）｜日本人形 出張買取LP

日本人形の出張買取サービス「買取 銭ちゃん」のランディングページです。
Instagram広告などからの流入を想定した、単一HTMLファイル（CSS・画像・JSすべて内包／外部依存なし）で構成されています。

## サービス概要

- 大阪府近郊対応の日本人形 出張買取サービス
- 1世帯5,000円保証でお引き取り（査定・出張・キャンセル料 無料）
- お引き取りした人形は海外（東南アジア中心）の子どもたちへ届けるリユース活動を実施

## ファイル構成

```
.
├── index.html      # LP本体（このファイルだけで完結）
├── README.md       # このファイル
└── .gitignore
```

`index.html` は画像を base64 で内包しているため、このファイル1つをどこに置いても、
そのまま開けば同じ見た目で表示されます（GitHub Pages でもローカルでも同様）。

## ローカルでの確認方法

`index.html` をダブルクリックしてブラウザで開くだけで確認できます。
サーバーを立てる場合は例えば以下でも構いません。

```bash
cd (index.htmlがあるフォルダ)
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

## 公開前に差し替えが必要な箇所

コード内に `<!-- 差し替え箇所：... -->` というコメントで明示しています。

| 項目 | 現在の状態 | 対応 |
|---|---|---|
| 電話番号（06-7410-0734） | 実際の番号を反映済み | 変更があれば `tel:` リンクと表示テキストの両方を修正 |
| 受付時間（9:00〜19:00） | 反映済み | 変更があれば全3箇所（ヒーロー下・フッター上部・フッター）を修正 |
| 古物商許可番号 | 未記入のプレースホルダー | フッター内のコメント箇所に実際の許可番号を入力（法令上、記載が必要です） |
| 予約フォームの送信先 | 未設定（`onsubmit="return false;"` で送信を停止中） | Googleフォームや外部フォームサービスに接続する場合、フォーム部分のコメントに従って `onsubmit` を削除し、`action` 属性または `fetch` 送信処理に置き換えてください |

## GitHubへの公開手順

### 1. リポジトリを作成してpush

**A. GitHub CLI（`gh`）を使う場合**

```bash
cd (index.html, README.md, .gitignore があるフォルダ)
git init
git add .
git commit -m "Initial commit: 銭ちゃん LP"
gh repo create senchan-lp --public --source=. --remote=origin --push
```

**B. GitHub上で先に空リポジトリを作る場合**

1. GitHub上で新規リポジトリを作成（例：`senchan-lp`、Public、README等は追加しない）
2. ローカルで以下を実行

```bash
cd (index.html, README.md, .gitignore があるフォルダ)
git init
git add .
git commit -m "Initial commit: 銭ちゃん LP"
git branch -M main
git remote add origin https://github.com/(あなたのユーザー名)/senchan-lp.git
git push -u origin main
```

### 2. GitHub Pagesで公開

1. GitHubのリポジトリページで **Settings** タブを開く
2. 左メニューの **Pages** を選択
3. **Build and deployment** の **Source** を `Deploy from a branch` に設定
4. **Branch** で `main` ブランチ・フォルダは `/ (root)` を選択して **Save**
5. 数分待つと、同じ画面に公開URL（`https://(ユーザー名).github.io/senchan-lp/`）が表示される

`index.html` がリポジトリのルート（一番上の階層）に置かれていれば、そのままこのURLで公開されます。

### 3. 更新時

```bash
git add .
git commit -m "更新内容のメモ"
git push
```

push後、数分でGitHub Pagesにも反映されます。

## 今後の改善候補

- 予約フォームの送信先を実際のフォームサービスに接続
- 古物商許可番号の記載
- Instagram広告からの流入計測用に、Google Analytics やMeta広告のコンバージョンタグを `</body>` 直前に追加
