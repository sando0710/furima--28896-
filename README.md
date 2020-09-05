# DB設計

## users table

|     Column      |  Type  |   Options             |
|-----------------|--------|-----------------------|
| mail            | string | unique:true,index:true|
| password        | string | null: false           |
| nickname        | string | null: false           |
| first_name      | string | null: false           |
| last_name       | string | null: false           |
| first_name_kana | string | null: false           |
| last_name_kana  | string | null: false           |
| birth_day       | date   | null: false           |

### Association

- has_many :items,dependent::destroy
- has_many :histories,dependent::destroy


## items table

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| user_id          | integer   | foreign_key:true             |
| name             | string    | null: false                  |
| introduction     | text      | null: false                  |
| category         | integer   | null: false                  |
| condition        | integer   | null: false                  |
| price            | integer   | null: false                  |
| delivery_burden  | integer   | null: false                  |
| prepare_days     | integer   | null: false                  |
| prefecture_code  | integer   | null: false                  |



### Association

- belongs_to :user
- belongs_to_active_hash :category
- belongs_to_active_hash :condition
- belongs_to_active_hash :delivery_burden
- belongs_to_active_hash :prepare_day
- belongs_to_active_hash :prefecture

## histories

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| user_id          | integer   | foreign_key:true             |
| item_id          | integer   | foreign_key:true             |


### Association

- belongs_to :user
- belongs_to_active_hash :prefecture
