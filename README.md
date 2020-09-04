# DB設計

## users table

|     Column      |  Type  |   Options   |
|-----------------|--------|-------------|
| nickname        | string | null: false |
| first_name      | string | null: false |
| last_name       | string | null: false |
| first_name_kana | string | null: false |
| last_name_kana  | string | null: false |
| birth_day       | date   | null: false |

### Association

- has_many :items,dependent::destroy
- has_many :cards

## items table

|    Column        | Type      | Options                      |
|------------------|-----------|------------------------------|
| name             | string    |                              |
| introduction     | text      |                              |
| category_id      | integer   | null: false,foreign_key:true |
| condition        | integer   |                              |
| price            | integer   |                              |
| delivery_burden  | integer   |                              |
| delivery_days    | integer   |                              |
| prefecture_id    | integer   |                              |
| user_id          | reference | foreign_key:true             |

### Association

- belongs_to :user
- has_one :item_purchases,dependent::destroy

## item_purchases table

|Column   | Type    | Options                     |
|---------|---------|-----------------------------|
| item_id |reference| null:false,foreign_key:true |
| user_id |reference| null:false,foreign_key:true |

### Association

- belongs_to :item
- belongs_to :user
- has_one :address

## cards table

| Column       | Type     | Options                     |
|--------------|----------|-----------------------------|
| postal_code  | string   |                             |
| prefecture_id| integer  | null:false                  |
| city         | string   |                             |
| address      | string   |                             |
| building     | string   |                             |
| phone_number | string   |                             |
| user_id      | reference| null:false,foreign_key:true |
| item_id      | reference| null:false,foreign_key:true |

### Association

- belongs_to :transaction

## user_purchases table

|Column   | Type    | Options                     |
|---------|---------|-----------------------------|
| card_id |reference| null:false,foreign_key:true |
| user_id |reference| null:false,foreign_key:true |

### Association

- belongs_to :user
