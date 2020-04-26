# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :join-Group
- has_many :Group-comments

## join-Group テーブル
|Column|Type|Options|
|------|----|-------|
|recently-text|text|null|
|member|string|null|
|title|text|null:false|
### Association
- belongs_to :users
- has_many :Group-comments

## Group-commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|string|null|
|user_id|integer|null: false, foreign_key: true|
|tweet_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :join-Group 
- belongs_to :users