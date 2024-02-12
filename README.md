---
### Задача 1. Таблица Staff. Получить список всех сотрудников, у которых в имени (name) есть буква 'a'.   

SELECT * FROM Staff  
WHERE name LIKE '%a%';  

---
### Задача 2. Таблица Staff. Получить список всех сотрудников, у которых зарплата  (salary) в промежутке от 8000 до 9000 (включительно).  

SELECT * FROM Staff  
WHERE salary BETWEEN 8000 AND 9000;  

---
### Задача 3. Таблица Staff. Получить список всех сотрудников (first_name), у которых длина имени больше 10 букв.  

SELECT * FROM Staff  
WHERE LENGTH(name) > 10;  

---
### Задача 4. Таблица Staff.  Получить список всех сотрудников (first_name),  которые пришли на работу (adopted) в 2008-ом году  

SELECT DISTINCT first_name FROM Staff  
WHERE adopted BETWEEN ‘01/01/2008’ AND ‘31/12/2008’;  

---
### Задача 5. Как получить детали описания объектов с ID 4 и 9 таблицы Trip?   

Ожидаемый результат:  

| ID  | title     | participants | habitation | total amount| rate |
| --- | --------- | ------------ | ---------- |------------ | ---  | 
| 4   | Service 1 | 12           | 10         | 6000        | 170  | 
| 9   | Service 2 | 48           | 54         | 23000       | 300  |

SELECT * FROM Trip  
WHERE ID in (4,9);   

---
### Задача 6.Как сформировать упорядоченный список первых 10 фамилий (surname) в таблице Trip участников клуба? В списке не должно быть повторений.  

Ожидаемый результат:  

| surname |        
| ------- | 
| Asanov  | 
| Berukov |
| Savicov |
| Serikov | 
| Sidorov | 
| Demidov | 
| Ivanov  | 
| Petrov  | 
| Radov   |
| Zaikov  |
  
SELECT DISTINCT surname FROM Trip  
ORDER BY surname LIMIT 10;            

---
### Задача 7. Найти средний возраст (age) всех пользователей (name) в базе данных (bd).  

SELECT name  AVG (age) FROM bd;  

---
### Задача 8. Получить список продуктов (products), цена (price) которых не превышает 1000 рублей.  

SELECT products FROM bd  
WHERE price <=1000;  

---

### Задача 9. Имеется две таблицы:  
* Таблица users : Хранит в себе данные пользователя: user_id , login , name , surname (идентификатор, логин, имя и фамилию)   
* Таблица pets : Содержит в себе информацию о питомцах пользователя: user_id, pet_id , type, nickname, breed (Идентификатор пользователя (внешний ключ), идентификатор животного, вид животного, его кличку и породу)
  Напишите SQL-запрос, возвращающий фамилию и имя всех владельцев котов Абиссинской (Abyssinian) породы. + Отсортировать по алфавиту  

SELECT DISTINCT (surname, name) FROM users JOIN pets  
ON users. user_id = pets. user_id  
WHERE type = ‘Abyssinian’  
ORDER BY surname;  

---

### Задача 10. Найти клиентов, которые совершили больше всего заказов.  

SELECT * FROM bd  
WHERE orders= (SELECT MAX(orders) FROM bd);  

---
	
