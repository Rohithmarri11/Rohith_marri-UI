Database: obs


users
||
||
\\
  ==>  customer
  ==>  vendor


users table
------------

Contents to be in user table

sno     column                  datatype        constrain                   default
---     -------                 ---------       ----------                  --------
1       user_id                 int             primary key auto_increment  -     
2.      first_name              varchar2(50)    not null                    -
3.      last_name               varchar2(50)    not null                    -
4.      mobile_No               number(10)      unique, not null            -
5.      Zip_code                number(6)       not null                    -
6.      email_id                varchar2(100)   unique, not null            -
7.      user_password           varchar2(225)   not null                    -
8.      address                 varchar2(200)   not null                    -
9.      company_name            varchar2(50)    -                           null
10.     company_location        varchar2(200)   -                           null
11.     GST_No                  varchar2(20)    unique, not null            -
12.     user_type               varchar2(20)    not null, CHECK (user_type  -
                                                IN ('vendor', 'customer'))
13.     user_image              blob            -                           -
14.     gender                  varchar(6)      not null                    -    


books table
------------

Contents to be in books table

sno     column                  datatype        constrain                   default
---     -------                 ---------       ----------                  --------
1.      book id                 number          primary key                 -
2.      book isb No             varchar2(20)    unique, not null            -
3.      book name               varchar2(100)   not null                    -
4.      book description        varchar2(1000)  not null                    -
5.      book auther             varchar2(50)    not null                    -
6.      book category           varchar2(50)    not null                    -
7.      book price              number(10,2)    not null                    -
8.      publisher name          varchar2(50)    not null                    -
9.      book edition number     varchar2(10)    not null                    -
10.     vendor id               number          forign key(user id)         -
11.     book image              blob            not null                    -
12.     book qty                number          not null                    -


orders table
-------------

Containts to be in orders table

sno     column                  datatype        constrain                   default
---     -------                 ---------       ----------                  --------
1.      order id                number          primary key                 -
2.      customer id             number          forign key(user id)         -
3.      items                   JSON            not null                    -
4.      order date              date            not null                    -
5.      Shipment date           date            not nul                     -
6.      shipment location       varchar2(200)   not null                    -
7.      shipment zipcode        number(6)       not null                    -
8.      shipment country code   varchar2(3)     not null                    -
9.      payment type            varchar2(20)    not null                    -
10.     payment status          varchar2(20)    not null, CHECK (paymtstus  -
                                                IN ('success', 'failed'))
11.     order shipment statue   varchar2(20)    not null                    -
12.     is returned             varchar2(3)     not null, CHECK (isreturned 
                                                IN ('YES', 'NO'))           No

items - json object structure:-
    [{"book id", "qty"},{"book id", "qty"},.....]