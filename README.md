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

## usersテーブル
|column|type|options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false,unique:true|
|password|string|null: false|

### Association
- has_many :users_groups
- has_many :groups, through: :users_groups
- has_many :messages

## groupsテーブル
|column|type|options|
|------|----|-------|
|name|string|null: false,unique:true|

### Association
- has_many :users_groups
- has_many :users, through: :users_groups
- has_many :messages

## group_userテーブル
|column|type|options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|groups|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## messageテーブル
|column|type|options|
|------|----|-------|
|content|string|
|image|string|
|group|integer|foreign_key: true|
|user|integer|foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user