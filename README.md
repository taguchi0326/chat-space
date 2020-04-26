# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false,index: true|
### Association
- has_many :group
- has_many :comments

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null|
### Association
- belongs_to :users
- has_many :comments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null|
|image|string|null|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :group 
- belongs_to :user

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :group 
- belongs_to :user