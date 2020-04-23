# README

## users_table

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false, unique: true|
|user_password|string|null: false|
|user_image|string|
|introduction|text|
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birth_day|date|null: false|

### Association

- has_many :products dependent: :destroy
- has_one :destination dependent: :destroy
- has_one :card dependent: :destroy


## destination_table

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|post_code|string|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|address|string|null: false|
|building_name|string|
|phone_number|string|

### Association

- belongs_to :user


## card_table

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|customer_id|string|null: false|
|card_id|string|null: false|

### Association

- belongs_to :user


## category_table

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|

### Association

- has_many :products


## product_table

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|price|string|null: false|
|description|string|null: false|
|status|string|null: false|
|size|string|null: false|
|shipping_cost|string|null: false|
|shipping_days|string|null: false|
|prefecture_id|integer|null: false|
|judgment|string|
|category_id|integer|null: false, foreign_key: true|
|brand_id|integer|null: false, foreign_key: true|
|shipping_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association

- belongs_to :user
- belongs_to :category
- belongs_to :brand
- has_many :images
- belongs_to_active_hash :prefecture


## image_table

|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|product_id|integer|null: false, foreign_key: true|

### Association

- belongs_to :product


## brand_table

|Column|Type|Options|
|------|----|-------|
|name|string|index: true|

### Association

has_many :products