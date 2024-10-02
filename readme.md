## docker run --name mypostgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
## docker exec -it mypostgres psql -U postgres
=> create table
    create table datas(name varchar2(255),int id);

=> insert into data
    insert into datas (name,id) values('aman',34),('rajat','44'); # here the two columns inserted

=> delete from data
    DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';

=> alter table
    add column   >>> alter table datas add color varchar(255);
    change column_type  >>>  alter table datas alter column id type varchar(4);
    delete column >>> alter table datas drop column id;

=> UPDATE Statement
    update datas set name='Raj' where name='rajat';    # without where all record will be update

=> Delete all rows
    truncate table datas;

=> primary key
    create table customer(customer_id serial not null primary key,name varchar(30));

=> not equal (<>)
    select * from customers where name <> 'rajat';

=> LIKE operator (case sensitive)
    select name from customer where name LIKE 'm%';

=> ILIKE operator (case insensitive)
    select name from customer where name LIKE 'M%';

=> IN 
    select * form customer  where name IN ('Rajat');

=> BETWEEN
    select * from customer where age between 1970 and 2000

=> IS NULL
    select * from customer where model IS NULL

=> NOT  (it can be used together with LIKE, ILIKE, IN, BETWEEN, and NULL)

=> DISTINCT (return only distinct (different) values.)
    select distinct from name from customer

=> COUNT
    SELECT COUNT(DISTINCT country) FROM customers; 

=> ORDER BY ()
    select * from products order by price;

=> ORDER BY (descensing DESC)
    select * from products order by price DESC;

=> LIMIT (only N row recored )
    select * from customer LIMIT 20;

=> OFFSET ( clause is used to specify where to start selecting the records to return)
    select * from name limit 20 offset 40

=> MIN and MAX 
    select MIN(price) as columsn_name from products;
    select MAX(price) from products;

=> SUM  and AVG 
    select SUM(price) from table;
    select AVG(price) from table;
    SELECT AVG(price)::NUMERIC(10,2)FROM products;  // with two decimal average  
    
=> Concatenate Columns
    select F_name || '  ' || L_name AS name from data;

=> JOIN 
    select product_id from product INNER JOIN categories on product.id=categories.id

=> UNION (Operator is used to combine the result-set of two or more queries.)
            //
            They must have the same number of columns
            The columns must have the same data types
            The columns must be in the same order
            //
    select name from table_1 union select department from table_2

=> UNION ALL(return dublicate value also)
    select name from table_1 union select department from table_2

=> GROUP BY (The GROUP BY clause is often used with aggregate functions
        like COUNT(),
        MAX(),
        MIN(),
        SUM(),
        AVG()
        to group the result-set by one or more columns.)
    select mode ,count(payment) from tables group by (mode)

=> HAVING (The HAVING clause was added to SQL because the WHERE clause cannot be used with aggregate functions)
    select count(payment),mode group by mode having count(payment)>400 

=> EXIST (This operator is used to test for the existence of any record in a sub query)   
    SELECT customers.customer_name FROM customers WHERE EXISTS (SELECT order_id FROM orders WHERE customer_id = customers.customer_id);

=> ANY (The ANY operator allows you to perform a comparison between a single column value and a range of other values)
    select age from student where name = ANY(select name from student where name like '%M');

=> ALL (ALL means that the condition will be true only if the operation is true for all values in the range.)
    select age from student where name = ALL(select name from student where name like '%M');

=> CASE (like if else)
    select product_name,
    case
        when price>50 then'low'
        when price<50 then'high'
    ELSE
        'normal'
    from products;
    