# Sustech keke

**_Name: 周恒(Alan Chou)_**

**_Email: alanzhchou@gmail.com_**


## Part-1 Analysis
1. basic register and login **_[ auth ]_**
2. look/update my basic information and secuity information **_[ auth ]_**

***
3. look for all recently posts/specific type posts/specific tag posts **_[ auth ]_**
4. get comments under specific post
5. make comment on specific post **_[ auth ]_**

***
6. edit a post from my phone and save/send to server **_[ auth ]_**
7. look for all my posts/specific type posts **_[ auth ]_**

## Part-2 url and method

1. basic register and login **_[ auth ]_**

| num | short_name | discribe | Auth? | url | method | data |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| 1 | register | register a user [phone number/email] | y | /register | post | {account,password,name} |
| 2 | login | login and keep session | y | /login | post | {account,password,auth_code} |
| 3 | log out | log out and clear session | y | /logout | post | none |


2. look/update my basic information and secuity information **_[ auth ]_**

| num | short_name | discribe | Auth? | url | method | data |
| - | - | - | - | - | - | - |
|  |  |  |  |  |  |  |
| 1 | basic_info | query basic_info | y | /user/basic | get | none |
| 2 | security_info | query security_info | y | /user/ssecurity | get | none |
| 3 | update basic_info | update basic_info | y | /user/basic/update | post | {account new basic_info } |
| 4 | update password | update password | y | /user/password/update | post | {old password,new password} |
| 5 | update Auth | Auth reality  | y | /user/reality/update | post | { reality auth info } |
