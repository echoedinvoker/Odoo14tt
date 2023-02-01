# **_Chapter 8: Relations Between Models_**

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

![Alt note: goal type](pic/01.jpg)

- A property can have one type, but the same type can be assigned to many properties. This is supported by the many2one concept.

- A many2one is a simple link to another object.

  - example: `partner_id = fields.Many2one("res.partner", string="Partner")`

    - It is a field, which is linked to "res.partner".

    - By convention, Many2one field names have the "\_id" suffix.

- In practice a many2one can be seen as a dropdown list in a form view.

- See also: [foreign keys](https://www.postgresql.org/docs/current/tutorial-fk.html)

### _Exercise: Add the Real Estate Property Type table_

![Alt lvim type.py](pic/02.jpg)

![Alt edit contents of type.py](pic/03.jpg)

![Alt lvim __init__.py](pic/04.jpg)

![Alt import type.py](pic/05.jpg)

![Alt lvim ir.model.access.csv](pic/06.jpg)

![Alt edit type to access right](pic/07.jpg)

![Alt lvim type_views.xml](pic/08.jpg)

![Alt edit action and form view records of type](pic/09.jpg)

![Alt lvim menus.xml](pic/10.jpg)

![Alt add type to setting list](pic/11.jpg)

![Alt lvim __manifest__.py](pic/12.jpg)

![Alt load data file type_view.xml](pic/13.jpg)

![Alt launch server](pic/14.jpg)

![Alt page check settings/types](pic/15.jpg)

![Alt page type action page](pic/16.jpg)

![Alt lvim estate_property.py](pic/17.jpg)

![Alt add type_id field (Many2one)](pic/18.jpg)

![Alt add type_id field (Many2one)2](pic/19.jpg)

![Alt lvim property_views.xml](pic/20.jpg)

![Alt add type_id to from and search views records](pic/21.jpg)

![Alt add type_id to tree views record](pic/22.jpg)

![Alt launch](pic/23.jpg)

![Alt page property list view check](pic/24.jpg)

![Alt page property form view check](pic/25.jpg)

![Alt page property search view check](pic/26.jpg)

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

### _Exercise: Add the buyer and the salesperson_

![Alt exercise: add the buyer and the salesperson](pic/27.jpg)

![Alt note: self](pic/28.jpg)

![Alt lvim buyer.py](pic/29.jpg)

![Alt edit contents of buyer model](pic/30.jpg)

![Alt lvim salesperson.py](pic/31.jpg)

![Alt edit contetns of salesperson model](pic/32.jpg)

![Alt lvim __init__.py](pic/33.jpg)

![Alt import above two model](pic/34.jpg)

![Alt lvim ir...](pic/35.jpg)

![Alt add access rights of above two model](pic/36.jpg)

![Alt launch ORM works](pic/37.jpg)

![Alt lvim property.py](pic/38.jpg)

![Alt example about self](pic/39.jpg)

![Alt add buyer and salesperson to property model](pic/40.jpg)

![Alt launch](pic/41.jpg)

![Alt lvim property_views.xml](pic/42.jpg)

![Alt create new page in Form views record of property xml](pic/43.jpg)

![Alt launch](pic/44.jpg)

![Alt page check page "more info"](pic/45.jpg)

## **Many2many**

[Reference](https://www.odoo.com/documentation/14.0/developer/reference/addons/orm.html#odoo.fields.Many2many)

![Alt note: goal - tag](pic/46.jpg)

- A property can have many tags and a tag can be assigned to many properties. -> **Many2many**

- By convention, Many2many fields have the **\_ids** suffix.

### _Exercise: Add the Real Estate Property Tag table_

![Alt exercise: add the real estate property tag table](pic/47.jpg)

![Alt lvim tag.py](pic/48.jpg)

![Alt edit contents of tag.py](pic/49.jpg)

![Alt lvim init](pic/50.jpg)

![Alt lvim import tag model](pic/51.jpg)

![Alt lvim property.py](pic/52.jpg)

![Alt add tag field (Many2many)](pic/53.jpg)

![Alt lvim ir](pic/54.jpg)

![Alt add access right to tag](pic/55.jpg)

![Alt launch ORM work](pic/56.jpg)

![Alt lvim tag_views.xml](pic/57.jpg)

![Alt edit action and from view records of tag](pic/58.jpg)

![Alt lvim menus.xml](pic/59.jpg)

![Alt add tag to settings list](pic/60.jpg)

![Alt __manifest__.py import tag_views.xml](pic/61.jpg)

![Alt launch](pic/62.jpg)

![Alt page check setting / tages](pic/63.jpg)

![Alt page check tages form view](pic/64.jpg)

![Alt example of tag widget](pic/65.jpg)

![Alt add tag widget to property form view record](pic/66.jpg)

![Alt page check form view of property (tags)](pic/67.jpg)

![Alt try to remove string tag by remove string conf inside property model](pic/68.jpg)

![Alt failed](pic/69.jpg)

## **One2many**

[Reference](https://www.odoo.com/documentation/14.0/developer/reference/addons/orm.html#odoo.fields.One2many)

![Alt note goal offer](pic/70.jpg)

- An offer applies to **one** property, but the same property can have **many** offers.

  - inverse of Many2one

- example: `test_ids = fields.One2many("test.model", "partner_id", string="Tests")`

  - first parameter = comodel

    - comodel is the abbreviation of "co-model", which is a term used in the Odoo framework to refer to the model that is related to the current model.

    - We use **res.partner** to be comodel in this case (real estate).

      - res.partner is a model in Odoo which is used to store information about people, companies and other entities. It is a core model of Odoo and is used in many other models.

  - second parameter

    - is the field we want to inverse

- By convention, one2many fields have "\_ids" suffix.

- **DANGER** Because a One2many is a virtual relationship, there must be a Many2one field defined in the comodel.

  - [ASK AI: One2many and Comodel](https://platform.openai.com/playground/p/yb51guPVIJhAkie9yoWoh6is)

### _Exercise: Add the Real Estate Offer table_

![Alt exercise: add real estate property offer table](pic/71.jpg)

![Alt lvim offer.py](pic/72.jpg)

![Alt edit contents of offer model](pic/73.jpg)

![Alt import offer modey by init](pic/74.jpg)

![Alt add access right of offer model](pic/75.jpg)

![Alt add new field offer_ids about offer model in property model](pic/76.jpg)

![Alt edit offer action and tree  view records](pic/77.jpg)

![Alt import offer xml by __manifest__.py](pic/78.jpg)

![Alt edit menus.xml to add offer list to advertisement](pic/79.jpg)

![Alt page check advertisement/offer action](pic/80.jpg)

![Alt page check offer action](pic/81.jpg)

![Alt property views xml - add new page to form view record](pic/82.jpg)

![Alt page check property form view (offers page)](pic/83.jpg)

![Alt edit offer views xml - remove field property_id](pic/84.jpg)

![Alt page check it works](pic/85.jpg)

**We don't need action or menu for all model**

![Alt offer view xml - remove action](pic/86.jpg)

![Alt menus xml - remove offer from adv](pic/87.jpg)

![Alt page check only accessible from property's form view](pic/88.jpg)

- So View records in XML for offer model only left List view, but server still work properly.

- It means we only access offer model from Form view of estate property.

  - It is normal some model always access by other model.
