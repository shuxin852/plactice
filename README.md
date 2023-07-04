# テーブル設計

## users テーブル

| Column        | Type       | Options                   |
| ------------- | ---------- | ------------------------- |
| username      | string     | null: false               |
| email         | string     | null: false, unique: true |
| password      | string     | null: false               |

### Association

- has_many :posts
- has_many :comments
- has_many :favorites
- has_many :likes
- has_many :follows

## posts テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| title         | string     | null: false                    |
| describe      | text       | null: false                    |

### Association

- has_many :comments
- has_many :favorites
- has_many :likes
- belongs_to :user

## comments

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| post          | references | null: false, foreign_key: true |
| content       | text       | null: false                    |

### Association

- belongs_to :user
- belongs_to :post

## relationships

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| follower      | references | null: false, foreign_key: true |
| following     | references | null: false, foreign_key: true |

### Association

- belongs_to :user

## favorites テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| post          | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :post

## likes テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| post          | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :post