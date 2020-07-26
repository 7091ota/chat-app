#テーブル設計


## usersテーブル
| column   |type    | options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |
### Association
- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages


## roomsテーブル
  | column | type   | options     |
  | ------ | ------ | ----------- |
  | name   | string | null: false |
### Association
- has_many :rooms_users
- has_many :users, through: rooms_users
- has_many :messages


## rooms_users
| column  | type      | options                        |
|-------- | --------- | ------------------------------ |
| user_id | reference | null: false, foreign_key: true |
| room_id | reference | null: false, foreign_key: true |
### Association
- belongs_to :users
- belomgs_to :rooms


## message
| column  | type       | options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |
| user_id | references | null: false, foreign_key :true |
| room_id | references | null: false, foreign_key :true |
### Association
- belongs_to :users
- belongs_to :rooms