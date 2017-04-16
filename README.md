# ChatSpace DataBase Design


Ruby 2.3.1

Rails 5.0.1

---

## ASSOCIATION


### Message

  belongs_to :user
  belongs_to :group


### User

  has_many :messages
  has_many :groups, through: :users_groups


### Group

  has_many :messages
  has_many :users, through: :users_groups


### UserGroup

  belongs_to :user
  belongs_to :group

---

## DATABASE


### Users
(created by devises)

| column   | type    | NULL | information   |
|:---------|:--------|:-----|:--------------|
| id       | integer | FALSE| 主キー         |
| name     | string  | FALSE| ユーザ名        |


### Massages
(created by CarrierWave)

| column          | type    | NULL | information   |
|:----------------|:--------|:-----|:--------------|
| id              | integer | FALSE| 主キー         |
| user_id         | integer | FALSE| 投稿したユーザのID (外部キー)        |
| group_id        | integer | FALSE| 送り先のgroupのID (外部キー、index) |
| text            | text    |      |   内容                           |
| image           | text    |      |   画像                           |


### Groups
| column | type    | NULL | information   |
|:-------|:--------|:-----|:--------------|
| id     | integer | FALSE|  主キー        |
| name   | string  | FALSE|  グループ名     |


### UsersGroups
| column   | type    | NULL | information   |
|:---------|:--------|:-----|:--------------|
| id       | integer | FALSE|   主キー       |
| user_id  | integer | FALSE|   外部キー     | 
| group_id | integer | FALSE|   外部キー     |
