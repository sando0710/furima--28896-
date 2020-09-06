# DB設計

## users table (ユーザー情報)

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
- has_many :exchanges,dependent::destroy


## items table (商品情報)

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| user_id          | integer   | foreign_key:true             |
| name             | string    | null: false                  |
| introduction     | text      | null: false                  |
| category         | integer   | null: false                  |
| condition        | integer   | null: false                  |
| delivery_burden  | string    | null: false                  |
| prefecture_code  | string    | null: false                  |
| prepare_days     | integer   | null: false                  |
| price            | integer   | null: false                  |

### Association

- belongs_to :user
- belongs_to_active_hash :category
- belongs_to_active_hash :condition
- belongs_to_active_hash :delivery_burden
- belongs_to_active_hash :prepare_day
- belongs_to_active_hash :prefecture
- has_one :exchange

## exchanges (購入管理情報)

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| user_id          | integer   | foreign_key:true             |
| item_id          | integer   | foreign_key:true             |
| sold_flag        | boolean   | null:false  defalut:false    |


### Association

- belongs_to :user
- belongs_to :item
- has_one :shipping

## shippings (配送先情報)

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| exchanges_id     | integer   | foreign_key:true             |
| post_code        | integer   | null: false                  |
| prefecture_code  | integer   | null: false                  |
| city             | string    | null: false                  | 
| address          | string    | null: false                  |
| building         | string    | null: false                  |
| phone_number     | integer   | null: false                  |
### Association 

- belongs_to :exchanges
- belongs_to_active_hash :prefecture