## **Unique constraint written as column constraint**

![Alt unique as column constraint](pic/01.jpg)

![Alt insert test](pic/02.jpg)

## **Unique constraint written as table constraint**

![Alt unique as table constraint](pic/03.jpg)

### _Defining unique constraint with multiple columns_

![Alt unique with multiple columns](pic/04.jpg)

![Alt insert test](pic/05.jpg)

## **Naming Unique constraint**

![Alt naming unique constraint](pic/06.jpg)

![Alt insert test](pic/07.jpg)

## **How about multiple nulls**

![Alt multiple nulls in different rows](pic/08.jpg)

## **Incomprehensible topics**

- Adding a unique constraint will automatically create a unique B-tree index on the column or group of columns listed in the constraint. A uniqueness restriction covering only some rows cannot be written as a unique constraint, but it is possible to enforce such a restriction by creating a unique partial index.

- NULLS NOT DISTINCT (syntax errors occur during practice)
