## **REFERENCE**

> We use REFERENCE this keyword to create foreign key constraint, instead of FOREIGN KEY.

![Alt refer to](pic/01.jpg)

![Alt fk check](pic/02.jpg)

## **Features of Foreign key**

### _Allow null_

![Alt fk allow null](pic/03.jpg)

### _Omit reference column name_

![Alt default refer to pk](pic/04.jpg)

### _Multiple ..._

**Columns**

![Alt multiple columns of fk](pic/05.jpg)

**Foreign keys**

![Alt multiple fks](pic/08.jpg)

- When this is the case, of course, you can only use the table constraint format, and you must use the keyword FOREIGN KEY to specify the referencing columns.

  - So the keyword FOREIGN KEY is used to specify the referencing column, before we use the column constraint way to write so do not need to use it.

## **Node Structure**

![Alt node](pic/06.jpg)

![Alt node insert](pic/07.jpg)

## **ON DELETE**

### _RESTRICT_

![Alt on delete restrict](pic/09.jpg)

![Alt on delete restrict: delete referenced row](pic/10.jpg)

- The result is similar to the default NO ACTION, but the difference between the two is that:

  - The essential difference between these two choices is that NO ACTION allows the check to be deferred until later in the transaction, whereas RESTRICT does not.

### _CASCADE_

![Alt on delete cascade](pic/11.jpg)

![Alt on delete cascade: delete referenced row](pic/12.jpg)

![Alt refercing row delete auto](pic/13.jpg)
