# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


## DB設計

## users table

| Column              | Type       | Options                    |
| ------------------- | ---------- | -------------------------- |
| id(PK)              | default    | null: false, index: true   |
| name                | string     | null: false                |
| email               | string     | null: false                |
| encrypted_password  | string     | null: false                |
| first_name          | string     | null: false                |
| last_name           | string     | null: false                |
| birth_date          | date       | null: false                |
| profile             | text       |                            |

### Association

has_many :works
has_many :comments


## works table

| Column              | Type       | Options                    |
| ------------------- | ---------- | -------------------------- |
| title               | string     | null: false                |
| info                | text       | null: false                |
| user_id(FK)         | references | foreign_key: true          |

### Association

belongs_to :user
has_many :comments


## comments table

| Column              | Type       | Options                    |
| ------------------- | ---------- | -------------------------- |
| comment             | text       | null: false                |
| user_id(FK)         | references | foreign_key: true          |
| work_id(FK)         | references | foreign_key: true          |

### Association

belongs_to :user
belongs_to :work