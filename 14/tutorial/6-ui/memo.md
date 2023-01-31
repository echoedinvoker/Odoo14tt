# **_Chapter 6: Finally, Some UI To Play With_**

## **Data Files (XML)**

[Reference](https://www.odoo.com/documentation/16.0/developer/reference/backend/data.html#reference-data)

> Although CSV is easy and convenient, there are some formats such as HTML tags that cannot be attached, so XML is required.

![Alt tag record example](pic/01.jpg)

- The knowledge about data files introduced in the previous chapter can be applied to XML, except that XML is usually about view, so it is generally placed in the views folder.

![Alt note: if performance is important...](pic/02.jpg)

- The UI in Odoo is largely defined by creating and composing records defined in XML files.
  - common pattern is Menu > Action > View.
    - user navigates through several menu levels; then the deepest level is an action which triggers the opening of the list of the records.

## **Actions**

[Reference](https://www.odoo.com/documentation/16.0/developer/reference/backend/actions.html#reference-actions)

### _Three ways to trigger actions_

1.  by clicking on menu item (linked to specific actions, we only cover this one in this chapter)
2.  by clicking on buttons in views (if these are connected to actions)
3.  as contextual actions on object

### _Link between Menu and Model_

> Action works like the link between Menu and Model.

![Alt smallest action record in .xml](pic/04.jpg)

- **id** = external identifier
- **model** = must be "ir.actions.act_window"
- **name** = name of action, as you wish.
- **res_model** = the model which this action applied to.
- **view_mode** = the views that will be available.

**real example - CRM action**
![Alt crm action record sample](pic/05.jpg)

### _Excercise: Add an action applied to our model_

**Instructions**
![Alt exercise: add an action applied to our model](pic/06.jpg)

**Correct directory**
![Alt create xml in correct directory](pic/07.jpg)

**Record in XML**
![Alt edit contents of action record in xml file](pic/08.jpg)

**\_\_manifest\_\_.py list it**
![Alt load it in __manifest__.py](pic/09.jpg)

**LOG:AssertionError**
![Alt LOG: AssertionError: Document does not comply with schema](pic/10.jpg)

![Alt add tag "odoo" in top level](pic/11.jpg)

![Alt LOG: successful load xml](pic/12.jpg)

## **Menus**

[Reference](https://www.odoo.com/documentation/16.0/developer/reference/backend/data.html#reference-data-shortcuts)

### _Goal: Three level architecture_

![Alt note: Goal - three level arch](pic/13.jpg)

### _Smallest Menu Record sample (one level)_

![Alt smallest menu record sample ](pic/14.jpg)

- There is a tag dedicated to create menu, so there is no need to have "model=" as in the case of action creation.
- The above is the simplest menu with only one level, so it must be linked to an action.

### _Three Level Menu_

![Alt three level image with note](pic/15.jpg)

![Alt smallest "three level" menu record sample](pic/16.jpg)

- The top is a three-level menu, and the deepest layer must be linked to the action.

### _Exercise: Add menus_

**Instructions**
![Alt Exercise: add menus](pic/17.jpg)

**Correct directory**
![Alt create .xml for menus record in correct folder](pic/18.jpg)

**Contents of Menus Record in XML**
![Alt edit contents of menus record in xml](pic/19.jpg)

![Alt add tag odoo](pic/20.jpg)

**\_\_manifest\_\_.py list it**
![Alt load it in __manifest__.py](pic/21.jpg)

**LOG: success load**
![Alt LOG: success load](pic/22.jpg)

**Page overview**
![Alt page create](pic/23.jpg)

![Alt action page:  new ](pic/24.jpg)

## **Field, Attributes And View**

[Field Parameters](https://www.odoo.com/documentation/16.0/developer/reference/backend/orm.html#odoo.fields.Field)

![Alt note: goal - some requirements of action page](pic/25.jpg)

- So far we only use generic view for our real estate property advertisements, but in most case we need to fine-tune the view.
  - firt step is to make sure that:
    - some fields have a default value
    - some fields are read-only
    - some fields are not copied when duplicating the record
- In our real estate business case, we would like the following:
  - The selling price should be read-only (it will be automatically filled in later)
  - The availability date and the selling price should not be copied when duplicating a record
  - The default number of bedrooms should be 2
  - The default availability date should be in 3 months

### _Some New Attributes(configuration of fields)_

> Before moving further with the view design, let’s step back to our model definition. We saw that some attributes, such as required=True, impact the table schema in the database. Other attributes will impact the view or provide default values.

**Exercise: Add new attributes to the fields**

> "attributes" here are more like configurations, so it means configurations of fields.

![Alt exercise: add new attr to the fields](pic/26.jpg)

![Alt edit contents of model to add more configurations](pic/27.jpg)

![Alt docs: copy configuration](pic/28.jpg)

![Alt edit contents of model to add "copy" configuration](pic/29.jpg)

![Alt LOG: name "date" is not defined](pic/30.jpg)

![Alt edit contents of model to import dependencies](pic/31.jpg)

![Alt LOG: success](pic/32.jpg)

![Alt action page - works but wierd layout](pic/33.jpg)

### _Default Values_

![Alt field configuration sample](pic/34.jpg)

[Ask AI: Field Name](https://beta.openai.com/playground/p/lZ7J5AY8kXQi3F5GXHXYC0tx)

![Alt exercise: set default values](pic/35.jpg)

- already implemented above.
- today() is to return date.today(), just help us to save some codes.

### _Reserved Fields_

> A few field names are reserved for pre-defined behaviors. They should be defined on a model when the related behavior is desired.

[Reference](https://www.odoo.com/documentation/16.0/developer/reference/backend/orm.html#reference-orm-fields-reserved)

**active**

> default value is False, so if you add this field into the model and not set any value to it, the record created by this model will be hide.

![Alt exercise: add active field](pic/36.jpg)

![Alt edit contents of model to add "active" field](pic/37.jpg)

![Alt action page - create a record](pic/38.jpg)

![Alt menu page - nothing appear](pic/39.jpg)

![Alt menu page - filter inactive](pic/40.jpg)

![Alt menu page - records appear](pic/41.jpg)

![Alt exercise: set a default value for active field](pic/42.jpg)

![Alt edit contents of model to set "active" default True](pic/43.jpg)

**state**

> At the moment there is no clue about what to do in this Field, but documents said that it will be used later on for several UI enhancements.

![Alt exercise: add state field](pic/44.jpg)

![Alt docs: Model.state](pic/45.jpg)

![Alt edit contents of model to add "state" field](pic/46.jpg)

![Alt action page: "state" appear](pic/47.jpg)
