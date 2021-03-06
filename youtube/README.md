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



### group_users table
|Column| Type|Options|
|:-----|:----|:------|
| user_id | references | null :false, foreign_key :true |
| group_id | references | null :false, foreign_key :true |

### Association
-belongs_to :user
-belongs_to :group


### messages table
|Column|Type|Options|
|:-----|:---|:------|
| body | text |        |
| image | string |       |
| user_id | references | null :false, foreign_key :true |
| group_id | references | null :false, foreign_key :true |

### Association
belongs_to :user
belongs_to :group


### users table
|Column|Type|Options|
|:-----|:---|:------|
| name | string	| null :false, unique :true |
| email  |	string |	null :false, unique :true |

### Association
has_many :messages
has_many :groups_users
has_many :groups, through::group_users


### groups table
|Column	|Type	  |Options                         |
|:------|:------|:-------------------------------|
| name | string | null :false, unique :true, index |

### Association
has_many :messages
has_many :group_users
has_many :users through::group_users