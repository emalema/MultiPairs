# README

# アプリケーション名
MultiPairs (Multiplets + Pairs)
# アプリケーション概要
記事やレビューをシェアし、ユーザー同士でコミュニケーションを取ることで孤独感を解消して励まし合うことができる。

# 利用方法
## 記事投稿
1. トップページ（一覧ページ）のヘッダーからユーザー新規登録を行う
2. 新規投稿ボタンから、投稿内容（タイトル、詳細、カテゴリ、画像）を入力し投稿する
3. カテゴリーページごとに調べたいときはカテゴリーの詳細ページへのリンクを押す

## 他者に共感する、励ます
1. 一覧ページから投稿をクリックして、内容の詳細を確認する
2. コメント投稿ボタンから、投稿内容に関するコメントを投稿する
3. コメントを削除したい場合はコメント詳細ページから削除ボタンを押す

# アプリケーションを作成した背景
自身も一卵性双生児の女児を出産し、壮絶な乳児期を経て日々の育児と家事や仕事を両立してきたことがきっかけ。
ハイリスク妊娠のため不安を抱え切迫早産により緊急入院するなどトラブル続きで情報収集が出来なかったことや、
産後は1日に授乳16回、おむつ24回の交換など寝る暇もないまま手探りで双子育児を経験したことで情報共有の難しさを痛感。
単胎児とは必要な情報が違いすぎて通常のサイトやアプリでは参考にできず、毎日多胎について検索していたことにより、
多胎家庭をターゲットとしたアプリを作成したいと考えて会員制交流アプリを作成するに至りました。
育児、教育、お金など多胎特有の問題が出てくることが多い家庭の一助となるようなアプリであれば嬉しいです。


# 洗い出した要件
要件を定義したシート
https://docs.google.com/spreadsheets/d/1jejkeB5Ot8OtcxgFfxO1bNIL5NxaYQEiESe_PTKWZkw/edit#gid=982722306

# 実装予定の機能
1. 育児用品のレビュー等の投稿の際には、フリマ機能と連携して購入できるようにする
2. 商品や場所の投稿の際にはリンクを設定して実際にページに遷移できるようにする

# データベース設計


# 開発環境
- Language：Swift
- Version：5.7.1
- Xcode：15.0.1
- URL：[App Store](https://apps.apple.com/jp/app/xcode/id497799835?mt=12)
- Architecture：MVVM

#　画面遷移図	画面遷移図を添付。
# ローカルでの動作方法※	git cloneしてから、ローカルで動作をさせるまでに必要なコマンドを記載。
# 工夫したポイント※	制作背景・使用技術・開発方法・タスク管理など、企業へＰＲしたい事柄を記載。

- Language：Swift
- Version：5.7.1
- Xcode：15.0.1
- URL：[App Store](https://apps.apple.com/jp/app/xcode/id497799835?mt=12)
- Architecture：MVVM

## 使用した技術

## リファレンス


# DB設計

## users table

| Column             | Type       | Options                                |
| ------------------ |----------  |--------------------------------------- |
| name               | string     | null:false                             |
| nickname           | string     | null:false                             |
| email              | string     | null:false,unique:true                 |
| date_of_birth      | date       | null:false                             |

## Association
- has_many :posts
- has_many :comments

## posts table

| Column             | Type       | Options                                |
| ------------------ |----------  |--------------------------------------- |
| name               | string     | null:false                             |
| price              | integer    | null:false                             |
| description        | text       | null:false                             |
| item_condition_id  | integer    | null:false                             |
| category_id        | integer    | null:false                             |
| shipping_fee_id    | integer    | null:false                             |
| prefecture_id      | integer    | null:false                             |
| shipping_date_id   | integer    | null:false                             |
| user               | references | null:false ,foreign_key:true           |

## Association
- belongs_to :user
- has_one:order

## comments table

| Column             | Type       | Options                                |
| ------------------ |----------  |--------------------------------------- |
| user               | references | null:false,foreign_key:true            |
| item               | references | null:false,foreign_key:true            |

## Association
- belongs_to :user
- belongs_to :item
- has_one :payment


## payments table

| Column             | Type       | Options                                |
| ------------------ |----------  |--------------------------------------- |
| post_code          | string     | null:false                             |
| prefecture_id      | integer    | null:false                             |
| city               | string     | null:false                             |
| address            | string     | null:false                             |
| building           | string     |                                        |
| phone_number       | string     | null:false                             |
| order              | references | null:false,foreign_key:true            |

## Association
- belongs_to :order
