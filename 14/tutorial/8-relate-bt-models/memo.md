# ***Chapter 8: Relations Between Models***

> In any real business scenario we need more than one model. Moreover, links between models are necessary.

**In our real estate module, we want the following models:**

- the customer who bought the property

- the real restate agent who sold the property

- the property type:

  - house
  - apartment
  - penthouse
  - castle
  - ...

- a list of tags characterizing the property:

  - cozy
  - renovated
  - ...

- a list of the offers received

## **Many2one**

[Reference](https://www.odoo.com/documentation/16.0/developer/reference/backend/orm.html#odoo.fields.Many2one)

pic goal

- A property can have one type, but the same type can be assigned to many properties. This is supported by the many2one concept.

- A many2one is a simple link to another object.

  - example: `partner_id = fields.Many2one("res.partner", string="Partner")`

    - It is a field, which is linked to "res.partner".

    - By convention, Many2one field names have the "_id" suffix.

- In practice a many2one can be seen as a dropdown list in a form view.

- See also: [foreign keys](https://www.postgresql.org/docs/current/tutorial-fk.html)

### _Exercise: Add the Real Estate Property Type table_

pic: exercise

pic: practice - add type model and ui

pic: practice - add type field to main model and its form

### _Another Two Pieces We misses_

- Two other informations we want on property:

  - **buyer**

    - can be any individual

  - **salesperson**

    - must be employee of real estate agency

- Related to this part of the topic, here are two models that we often refer to:

  - **res.partner**

    - is a physical or legal entity, so it can be:

      - a company
      - an individual
      - even just a contact address

  - **res.users** - users of the system

    - internal - have access to the Odoo backend
    - portal - cannot access the backend, only the frontend
      - e.g. to access their previous orders in eCommerce
  
### _Exercise: Add the buer and the salesperson_

pic - exercise
pic - note for hint



