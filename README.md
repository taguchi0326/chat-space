# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false,index: true|
### Association
- has_many :groups, through: :groups_users
- has_many :comments
- has_many :groups_users

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :comments
- has_many :groups_users
- has_many :users, through: :groups_users

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|
|image|string|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user