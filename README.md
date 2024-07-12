CREATE Table Publishers(
publisher_id int primary key identity(1,1),
publisher_name varchar (50) not null,

)

insert into Publishers values("Bloomsberry");
insert into Publishers values("Rupa & Co");
insert into Publishers values("Apeejay");
insert into Publishers values("Alchemist");

select * from Publishers;



CREATE Table categories(
category_id int primary key identity(1,1),
category_name varchar (50) not null,

)
insert into categories values("Fantasy");
insert into categories values("Love story");
insert into categories values("Fantasy");
insert into categories values("History");
select * from categories;



CREATE Table  users(
user_id int primary key identity(1,1),
user_name varchar (20) not null,
email varchar(20)unique not null,
phone_number varchar(20)unique not null,

)
insert into users values("Riya","riya123@gmail.com","9178197056");
insert into users values("Priya","priya123@gmail.com","9178197057");
insert into users values("Sriya","sriya123@gmail.com","9178197055");
insert into users values("Kriya","kriya123@gmail.com","9178197059");
select * from users;


CREATE TABLE Books(
book_id int primary key identity(1,1),
Title varchar (20) not null,
ISBN varchar (20)  unique not null,
Publication_year varchar (10) not null,
Publisher_id  int foreign key references publishers(publisher_id) on delete cascade,
Category_id  int Foreign key references categories(category_id) on delete cascade,
Author_Name varchar(20)check (Author_Name is not null),

)

insert into Books values("Harry Potter","0-7475-9105-9","2007",1,1,"J.k Rowling");
insert into Books values("Half girlfriend","978-81-291-375","2014",2,2,"Chetan Bhagat");
insert into Books values("The Da Vinci ","0-7488-9105-9","2007",3,3,"Stephenie Meyer");
insert into Books values("War & Peace","2-8878-9105-9","1819",4,4,"Dan Brown");



select * from Books;


CREATE Table  borrowings(
borrow_id int primary key identity(1,1),
borrow_date date not null,
return_date date not null,
user_id  int foreign key references users(user_id) on delete cascade,
book_id  int foreign key references books(book_id) on delete cascade
)

insert into borrowings values ("2023-12-12","1.6.2024",1,1);
insert into borrowings values ("2023-1-2","2.7.2024",2,2);
insert into borrowings values ("2023-2-3","6.6.2024",3,3);
insert into borrowings values ("2023-5-6","8.9.2024",4,4);
select * from borrowings;
