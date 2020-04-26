# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :Group
- has_many :comments

## Group テーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null|
### Association
- belongs_to :users
- has_many :comments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|string|null|
|user_id|integer|null: false, foreign_key: true|
|Group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :Group 
- belongs_to :users

## groups_usersテーブル
|Column|Type|Options|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :Group 
- belongs_to :users