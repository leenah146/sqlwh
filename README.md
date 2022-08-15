create database store;

create table countries (
 code int primary key ,
name varchar(20) unique ,
 continent_name varchar(20) not null 
);
create table users (
 id int primary key ,
 full_name varchar(20) not null ,
 email varchar(20) unique not null ,
 gender char(1) check ( gender='m' or gender='f' ),
 date_of_birth varchar(15),
 created_at datetime,
 country_code int,
foreign key(country_code)references countries(code)
);
create table orders (
 id int primary key ,
 user_id int  ,
 status char(6) check (status='start' or status='finish' ),
 created_at datetime,
 foreign key(user_id)references users(id)
);
create table products (
 id int primary key,
 name varchar(10) not null,
 price int default 0,
 status varchar(10)check (status='valid' or status='expired' ),
 created_at datetime
);
create table order_products (
 order_id int,
 product_id int,
 quantity int default 0,
 foreign key(order_id)references orders(id),
 foreign key(product_id)references products(id)
);
insert into countries values (10,'ryiadh','ryiadh');
insert into countries values (9,'onaizah','qaseem');
insert into users values ('1', 'leenah', 'leenah@gmail.com', 'f', '14/6/1997', '2022-08-15', '10');
insert into users values ('2', 'sara', 'sara@gmail.com', 'f', '14/6/2000', '2022-08-14', '10');
insert into orders values ('2', '1', 'start', '2022-08-15');
insert into products values ('40', 'phone', '4000', 'valid', '2020-08-03 ');
insert into order_products values ('2', '40', '3');
update countries set name = 'buryadah' WHERE code = 9;
delete from products where id=40;
