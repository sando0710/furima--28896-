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
- has_many :transactions

## items table

|    Column     | Type      | Options                      |
|---------------|-----------|------------------------------|
| name          | string    | null: false                  |
| introduction  | text      | null: false                  |
| category_id   | integer   | null: false,foreign_key:true |
| condition     | integer   | null: false                  |
| price         | integer   | null: false                  |
| delivery_fee  | integer   | null: false                  |
| delivery_days | integer   | null: false                  |
| prefecture_id | integer   | null: false                  |
| user          | reference | foreign_key:true             |

### Association

- belongs_to :user
- belongs_to :category
- belongs_to :prefecture
- belongs_to :transaction,dependent::destroy

## Transactions table

|Column   | Type    | Options                     |
|---------|---------|-----------------------------|
| item    |reference| null:false,foreign_key:true |
| user    |reference| null:false,foreign_key:true |
| address |reference| null:false,foreign_key:true |

### Association

- belongs_to :item
- belongs_to :user
- has_one :address

## Addresses table

| Column       | Type     | Options                     |
|--------------|----------|-----------------------------|
| postal_code  | string   | null:false                  |
| prefecture   | integer  | null:false                  |
| city         | integer  | null:false                  |
| address      | string   | null:false                  |
| phone_number | string   | null:false                  |
| transaction  | reference| null:false,foreign_key:true |

### Association

- belongs_to :transaction
#aaa