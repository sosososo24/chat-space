# Chat_space DB 設計
## usersテーブル
|Colum|Type|Options|
|-----|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :groups, through: groups_users
- has_many :groups_users

## groupsテーブル
|Colum|Type|Options|
|-----|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users, through: groups_users
- has_many :groups_users

## groups_usersテーブル
|Colum|Type|Options|
|-----|----|-------|
|user_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## messageテーブル
|Colum|Type|Options|
|-----|----|-------|
|body|text|
|image|string|
|user_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
