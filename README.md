# テーブル設計

## users テーブル

| Column       | Type      | Options                   |
| -----------  | --------- | ------------------------- |
| nickname     | string    | null: false               |
| email        | string    | null: false, unique: true |
### Association
- has_many :topics
- has_many :comments

## topics テーブル
| Column       | Type       | Options                   |
| -----------  | ---------- | ------------------------- |
| nickname     | string     | null: false               |
| shop_name    | string     | null: false, unique: true |
| price        | integer    | null: false               |
| text         | string     | null: false               |
| user         | references | null: false, FK:true      |
### Association
- belongs_to :users
- has_many :comments

## comments テーブル
| Column       | Type       | Options                   |
| -----------  | ---------- | ------------------------- |
| user         | references | null: false, FK:true      |
| topics       | references | null: false, FK:true      |
### Association
- belongs_to :user
- belongs_to :comments

## categories (Active Hash)
| Column            | Type      | Options                  |
| ----------------  | --------- | ------------------------ |
| category          | integer   | null: false              |