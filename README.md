# EkaterinaVSH.github.io
ДЗ 3

--Напишите запрос, который выводит список фильмов, где рейтинг является NULL, и заменяет NULL на значение 0
select * FROM movies where rating is null 

update movies set rating=NULL where movie_id='28'

select title, coalesce(rating,0) as rating from movies where rating is null;


--Напишите запрос, который выводит название фильма и округленное вверх значение рейтинга до ближайшего целого числа.
select title, ceil(rating) as rating_rounded_up from movies where rating is not null

--Выведите список клиентов, которые зарегистрировались в последний месяц.

select first_name, last_name, registration_date from customers c 
where registration_date >= CURRENT_DATE -interval '30 days'
order by registration_date desc;

--Выведите количество дней, в течение которых каждый клиент держал у себя фильм.

select c.first_name, c.last_name , (rentals.return_date-rentals.rental_date) as days_rented 
from customers c
join rentals  on c.customer_id =rentals.customer_id 
where rentals.return_date is not null 
order by c.customer_id , rentals.rental_date;

--Напишите запрос, который выводит название фильма в верхнем регистре.
select UPPER(title) from movies;

