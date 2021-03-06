# テーブル設計

## users テーブル

| Column            | Type         | Options                        | 
| --------          | ------------ | ------------------------------ |
| nickname          | string       | null: false                    |
| email             | string       | null: false                    |
| encrypted_password| string       | null: false                    |   
| birth_date  　　　 | date         | null: false                    |   
| first_name        | string       | null: false                    |
| last_name         | string       | null: false                    |
| first_name_kana   | string       | null: false                    |      
| last_name_kana    | string       | null: false                    |  

**Association**

* has_many :items
* has_many :orders

## items テーブル

| Column           | Type        | Options                      |
| -------------    | ----------- | ---------------------------- |                  
| title            | string      | null: false                  |
| detail           | text        | null: false                  |
| category_id      | integer     | null: false                  |
| condition_id     | integer     | null: false                  |
| postage_id       | integer     | null: false                  |
| prefecture_id    | integer     | null: false                  |
| delivery_day_id  | integer     | null: false                  |
| price            | integer     | null: false                  | 
| user             | references  | null:false, foreign_key: true|


**Association**

* belongs_to :user
* has_one :order
* belongs_to_active_hash :prefecture
* belongs_to_active_hash :category
* belongs_to_active_hash :condition
* belongs_to_active_hash :postage
* belongs_to_active_hash :delivery_day


## orders テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| item      | references | null: false, foreign_key: true |       
| user      | references | null: false, foreign_key: true |

**Association**

* belongs_to :user
* belongs_to :item
* has_one :address

## addresses　テーブル

| Column       | Type         | Options                        | 
| ------------ | ------------ | ------------------------------ |
| postal_code  | string       | null: false                    |
| prefecture_id| integer      | null: false                    |
| city         | string       | null: false                    |
| address      | string       | null: false                    |      
| apartment    | string       | default: ""       　　　　　　　　| 
| phone_number | string       | null: false                    |
| order        | references   | null: false, foreign_key: true | 

**Association**

* belongs_to_active_hash :prefecture
* belongs_to :order

<!-- ## prefectures テーブル

| Column       | Type         | Options                        | 
| --------     | ------------ | ------------------------------ |
| name         | string       | null: false                    |


## categories テーブル

| Column       | Type         | Options                        | 
| --------     | ------------ | -------------------------------|
| name         | string       | null: false                    |

## conditions　テーブル

| Column       | Type         | Options                        | 
| --------     | ------------ | ------------------------------ |
| value        | string       | null: false                    |

## postages テーブル

| Column       | Type         | Options                        | 
| --------     | ------------ | ------------------------------ |
| value        | string       | null: false                    |

## delivery_days テーブル

| Column       | Type         | Options                        | 
| --------     | ------------ | ------------------------------ |
| value         | string       | null: false                   | -->


