# movie-space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|index: true|
### Association
- has_many :groups, through: :groups_users
- has_many :group_users
- has_many :messages


# groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|index: true|
### Association
- has_many :users, through: :groups_users
- has_many :groups_users
- has_many :messages

# messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|movie|text||
|text|text||
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

