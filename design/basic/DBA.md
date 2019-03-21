# Sustech keke => DBA design

**_Name: 周恒(Alan Chou)_**

**_Email: alanzhchou@gmail.com_**

## Part-1 Analysis

#### Object atom => only the client side

> 1. user => ~1000-10000

> 2. Post Object => ~1000-5000/day

> 3. comments

> 4. Post Object types

> 5. Post Object tags

> 6. transaction table

> 7. *favorite Post table (work for AI algorithm)

> 8. *System config 
```
when face more users or infomation => module to many smaller parts
```

## Part-2 details design

> User table

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| User | 1 | id | int | unique/primary/auto increase |  |
|  | 2 | account | varchar(50) | unique |  |
|  | 3 | name | varchar(100) | unique | y |
|  | 4 | sex | int | NOT NULL |  | female/male/not show |
|  | 5 | bio | varchar(255) |  |  |  |
|  | 6 | avater_src | varchar(255) | unique |  |  |
|  | 7 | address | varchar(100) |  |  |  |
|  | 8 | contact | json |  |  |  |
|  | 9 | auth_infomation | json |  |  |  |
|  | 10 | password | varchar(255) | NOT NULL |  |  |
|  | 11 | create_date | Date | NOT NULL |  |  |


> Post table

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| Post | 1 | id | int | unique/primary/auto increase |  |
|  | 2 | title | varchar(100) | NOT NULL | y |  |
|  | 3 | type_id | int | NOT NULL |  |  |
|  | 4 | tags | array[int] | NOT NULL |  |  |
|  | 5 | describe | varchar(1000) | NOT NULL |  |  |
|  | 6 | post_user_id | int | NOT NULL |  |  |
|  | 7 | create_date | Date | NOT NULL |  |  |
|  | 8 | comments_id | array[int] |  |  |  |
|  | 9 | state | int | NOT NULL |  | save/post/destroy |
|  | 10 | favorite | boolean |  |  | strick to the top or not |
|  | 11 | imgs | json |  |  | img_name=>img_src |
|  | 12 | *hot_value | int |  |  | different class for showing |


> Comment table (not support img insert)

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| Comment | 1 | id | int | unique/primary/auto increase |  |
|  | 2 | content | varchar(255) | NOT NULL |  |  |
|  | 3 | post_object_id | int | NOT NULL |  |  |
|  | 4 | post_user_id | int | NOT NULL |  |  |
|  | 5 | son_comments | array[int] |  |  | hold son comments id |
|  | 6 | create_date | Date | NOT NULL |  |  |
|  | 7 | read_date | Date |  |  |  |

> PostType table (dynamically adding)

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| Type | 1 | id | int | unique/primary/auto increase |  |
|  | 2 | name | varchar(100) | unique/NOT NULL | y | the type name |
|  | 3 | discribe | varchar(255) | NOT NULL |  |  |
|  | 4 | son_post_types | array[int] |  |  | a widely type can contain others |
|  | 5 | create_date | Date | NOT NULL |  |  |

> PostTags table (dynamically adding)

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| tag | 1 | id | int | unique/primary/auto increase |  | | 
|  | 2 | name | varchar(50) | unique/NOT NULL |  |  |
|  | 3 | create_date | Date | NOT NULL |  |  |

> Transaction table 

| table_name | num | cols | type | key | index? | discribe |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| Transaction | 1 | id | int | unique/primary/auto increase |  | | 
|  | 2 | post_object_id | int | unique/NOT NULL |  | based on which post_object |
|  | 3 | poster_user_id | int | NOT NULL |  |  |
|  | 4 | finish_user_id | int | NOT NULL |  |  |
|  | 6 | create_date | Date | NOT NULL |  |  |
|  | 7 | finish_date | Date | NOT NULL |  |  |