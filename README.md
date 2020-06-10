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

##usersテーブル
|column|type|options|
|------|----|-------|
|name|string｜null: false|
|email|string|null: false,unique:true|
|password|string|null: false|

### Association
- has_many :groups
- has_many :message

##groupsテーブル
|column|type|options|
|------|----|-------|
|name|string｜null: false,add_index:true|
|user_id|integer|null: false,foreign_key: true|

### Association
- has_many :user
- belongs_to :message

##users_groupsテーブル
|column|type|options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|groups|integer|null: false, foreign_key: true|

### Association
- belongs_to :users
- belongs_to :groups


##messageテーブル
|column|type|options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|

### Association
- belongs_to :users