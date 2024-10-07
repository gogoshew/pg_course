1. Создадим таблицу workers:
```azure
   CREATE TABLE Workers (
    worker_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    gender VARCHAR(50) CHECK (gender IN ('Мужской', 'Женский')) NOT NULL,
    birthdate DATE NOT NULL
);
```
2. Наполним таблицу workers:
```azure
INSERT INTO Workers (name, gender, birthdate) VALUES
('Иван Иванов', 'Мужской', '1985-05-12'),
('Анна Смирнова', 'Женский', '1990-07-23'),
('Сергей Петров', 'Мужской', '1978-03-09'),
('Ольга Кузнецова', 'Женский', '1982-12-15'),
('Дмитрий Соколов', 'Мужской', '1995-09-30'),
('Елена Федорова', 'Женский', '1992-11-05'),
('Алексей Попов', 'Мужской', '1980-02-20'),
('Мария Морозова', 'Женский', '1988-08-11'),
('Николай Павлов', 'Мужской', '1993-01-17'),
('Татьяна Орлова', 'Женский', '1987-06-25');
INSERT 0 10
    
    worker_id |      name       | gender  | birthdate
-----------+-----------------+---------+------------
    1 | Иван Иванов     | Мужской | 1985-05-12
    2 | Анна Смирнова   | Женский | 1990-07-23
    3 | Сергей Петров   | Мужской | 1978-03-09
    4 | Ольга Кузнецова | Женский | 1982-12-15
    5 | Дмитрий Соколов | Мужской | 1995-09-30
    6 | Елена Федорова  | Женский | 1992-11-05
    7 | Алексей Попов   | Мужской | 1980-02-20
    8 | Мария Морозова  | Женский | 1988-08-11
    9 | Николай Павлов  | Мужской | 1993-01-17
    10 | Татьяна Орлова  | Женский | 1987-06-25
    (10 rows)
```

3. Структура созданной таблицы:
```azure
                                                                    Table "public.workers"
  Column   |          Type          | Collation | Nullable |                  Default                   | Storage  | Compression | Stats target | Description 
-----------+------------------------+-----------+----------+--------------------------------------------+----------+-------------+--------------+-------------
 worker_id | integer                |           | not null | nextval('workers_worker_id_seq'::regclass) | plain    |             |              | 
 name      | character varying(100) |           | not null |                                            | extended |             |              | 
 gender    | character varying(50)  |           | not null |                                            | extended |             |              | 
 birthdate | date                   |           | not null |                                            | plain    |             |              | 
Indexes:
    "workers_pkey" PRIMARY KEY, btree (worker_id)
Check constraints:
    "workers_gender_check" CHECK (gender::text = ANY (ARRAY['Мужской'::character varying::text, 'Женский'::character varying::text]))
Access method: heap
```

4. 
