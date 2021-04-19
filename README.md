# README

## users テーブル 

| Column   | Type               | Options     | 
| -------- | ------             | ----------- | 
| nickname             | string | null: false | 
| email                | string | null: false,unique: true | 
| encrypted_password   | string | null: false | 
| first_name           | string | null: false |            
| last_name            | string | null: false |             
| first_name_kana      | string | null: false | 
| last_name_kana       | string | null: false | 
| birth_date           |  date  | null: false |            

### Association 

- has_many :items 
- has_many :purchases

  
## items テーブル  

| Column     | Type                    | Options           | 
| ------     | ----------              | ------------      | 
| name                     | string    | null: false       | 
| item_information         | text      | null: false       | 
| brand                    | string    | null: false       |
| category_id              | integer   | null: false       |
| size_id                  | integer   | null: false       | 
| price                    | integer   | null: false       | 

| user | references | null: false, foreign_key: true | 


### Association 

- belongs_to :user 
- has_one    :purchase 


##  purchase テーブル
| Column         | Type       | Options             | 
| ------         | ---------- | ------------        | 
|  user          | references | foreign_key: true   | 
|  item          | references | foreign_key: true   | 

### Association 

- belongs_to :user
- belongs_to :item
- has_one    :shipping_address


##  shipping address テーブル 
| Column         | Type       | Options             | 
| ------         | ---------- | ------------        | 
| postal_code    | string     | null: false,        | 
| prefecture_id  | integer    | null: false,        | 
| city           | string     | null: false,        | 
| address        | string     | null: false,        | 
| phone_number   | string     | null: false,        | 
| building_name  | string     |                     |
 
| purchase | references | null: false, foreign_key: true | 

### Association 

- belongs_to :purchase
