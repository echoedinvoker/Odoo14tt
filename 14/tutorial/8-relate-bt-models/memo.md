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
