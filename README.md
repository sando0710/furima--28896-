# DB設計

## users table

|     Column      |  Type  |   Options             |
|-----------------|--------|-----------------------|
| id              |        |                     PK|
| mail            | syring | unique:true,index:true|
| nickname        | string |                       |
| first_name      | string |                       |
| last_name       | string |                       |
| first_name_kana | string |                       |
| last_name_kana  | string |                       |
| birth_day       | date   |                       |

### Association

- has_many :items,dependent::destroy
- has_many :cards

## items table

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| id               |           |                            PK|
| seller           | references| foreign_key:true             |
| buyer            | references| foreign_key:true             |
| name             | string    |                              |
| introduction     | text      |                              |
| category         | string    | null: false                  |
| condition        | string    | null: false                  |
| price            | integer   |                              |
| delivery_burden  | string    | null: false                  |
| perpare_days     | integer   | null: false                  |
| prefecture_code  | integer   | null: false                  |

### Association

- belongs_to :user
- has_one :item_purchases,dependent::destroy


## cards table

| Column            | Type     | Options                     |
|-------------------|----------|-----------------------------|
| id                |        PK|                           PK|
| user_id           | integer  | null:false                  |
| card_number       | integer  | unique:true                 |
| expiration_term   | date     | null:false                  |
| security_code     | integer  |                             |


### Association

- belongs_to :transaction

