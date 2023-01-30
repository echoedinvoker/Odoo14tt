## **Goal: Create table by ORM**

### _Goal_

![Alt Goal: automatically create a table "estate_property" in psql by ORM](pic/01.jpg)

### _Smallest model script_

![Alt smallest model example](pic/02.jpg)

- Odoo model is defined by Python class, which inherits "models.Model".

### _CRM model & file structure_

> The file structure required to load the model is more complex, requiring two **init**.py in different layers of the folder, so the following is a direct example using the CRM model "crm_recurring_plan".

![Alt CRM model example](pic/03.jpg)

![Alt __init__.py import 1](pic/04.jpg)

![Alt __init__.py import 2 & structure](pic/05.jpg)

### _Create file structure_

> The following practice is just to follow the above example to make it.

![Alt create file structure](pic/06.jpg)

### _Edit contents of model with smallest one_

![Alt edit model (smallest)](pic/07.jpg)

### _bottom layer **init**.py_

![Alt nvim __init__.py](pic/08.jpg)

![Alt edit __init__.py](pic/09.jpg)

### _uppter layer **init**.py_

![Alt nvim __init__.py](pic/10.jpg)

![Alt edit __init__.py](pic/11.jpg)

### _Update module & Check result in the database_

![Alt start server](pic/12.jpg)

![Alt check if module installed](pic/13.jpg)

- Make sure the module is installed before you can upgrade it.

![Alt re-launch server with updating module](pic/14.jpg)

![Alt log WARNINGs](pic/15.jpg)

![Alt check psql table exist or not](pic/16.jpg)

## **Exercise: Add \_description in model**

### _exercise instruction_

![Alt exercise: add _description to remove WARNINGs](pic/17.jpg)

### _Edit contents of model to add \_description_

![Alt edit model to add _description](pic/18.jpg)

### _Upgrade module and Check the results_

![Alt launch server and updating module to check LOG](pic/19.jpg)

## **Create Fields**

### _simplest sample_

![Alt build fields sample](pic/20.jpg)

- Creating fields relies on odoo's Fields class as above.

### _Goal & Exercise: add following fields & wanted results in database_

![Alt Goal:table Schema need to be](pic/21.jpg)

![Alt Exercise: Add following basic fields](pic/22.jpg)

**Type Selection**
![Alt check type Selection's example](pic/23.jpg)

- "help" is an optional configuration, which will be mentioned later.

### _Edit contents of model to add fields_

![Alt edit model to add fields](pic/24.jpg)

### _Upgrade Module & Check the results_

![Alt launch server to updating module](pic/25.jpg)

![Alt check Schema of table](pic/26.jpg)

## **Configure fields**

### _passing configuration as arguements_

![Alt the way to configure fields](pic/27.jpg)

### _Exercise: add bellow configuration to specific fileds_

![Alt Exercise: add some configuration to fields](pic/28.jpg)

![Alt edit model to add configuration to fields](pic/29.jpg)

### _Upgrade Module & Check the results_

![Alt launch server to updating module](pic/30.jpg)

![Alt check table Schema](pic/31.jpg)

## **Automatic Fields**

> Odoo creates a few fields in all models1. These fields are managed by the system and can’t be written to, but they can be read if useful or necessary.

- **id(Id)**
  - The unique identifier
- **create_date (Datetime)**
  - Creation date of the record.
- **create_uid (Many2one)**
  - User who created the record.
- **write_date (Datetime)**
  - Last modification date of the record.
- **write_uid (Many2one)**
  - User who last modified the record.
