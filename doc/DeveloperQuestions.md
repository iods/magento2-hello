<h1 align="center">Developer Questions</h1>
<br />
Some certification questions for help, separated by experience level.

| Workflow Name                                                 | Description                                                            |
| ------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [Integration Test](./.github/workflows/integration-README.md) | A Github Workflow that runs the Integration Tests of a Magento Package |

Junior
------

> What is Magento?

Magento is a feature-rich ecommerce platform built on open-source technology that provides online merchants with unprecedented
flexibility and control over the look, content, and functionality of their store. Magento's intuitive administrative interface
features powerful marketing, seo, and catalog-management tools for giving merchants the power to create sites tailored to their
unique business needs. Designed to be completely scalable and backed by community and Varien, Magento offers the ultimate solution.


> What is the difference between `Mage::getSingleton()` and `Mage::getModel()`?

Object creation. If an object is being created for the same class it won't be created again by utilizing the Singleton design
pattern. This is useful where you want to create an object once, fetch and continue to use it w/o creating a new object each and
every time. For instance, a session object. Values are added and removed from this object while a session traverses new pages,
but the object is never newly created. New objects lose changes.

For instances where new data is accessed each time the object is called, you would use `Mage::getModel()` which produces
a new object every time the class is called.


> What is the difference between the EAV and Flat Model tables in Magento?

Both models have large differences in how their schema stores data.

EAV is more of a normalized form of the database model. A primary feature of EAV based platforms is that columns values are stored in
their respective data type table. So product and catalog data can be stored in their respective tables. That means you would use SQL
joins to gather the data together. Bringing more complexity to the approach.

Flat is a single table, single query. Unlike EAV it is NOT segmented out into respective data types.


> What are some ways to optimize the Magento performance?

* Disable any unused modules
* Enable Magento caching
* Disable the Magento log
* Compile JS/CSS into one file
* MySQL query caching
* Enable gzip compression


> What is the Magento Payment Gateway?

A payment gateway processes the credit card data securely between a customer and the merchant, then between the merchant and the processor. It is
like a checkpoint between the two. It protects customers from attempting to collect personal and financial information from customers and the bank.


> What are some advantages of Magento 2

* Improved admin UI
* Improved upon file structure
* Improved performance and scalability over M1


> What are the steps for writing a Congruence\Standards module in Magento 2?

1. Create a  namespace in `app/code/`


### Layout

> Explain the concepts of handles in Magento?

Magento decides how the structure of pages will be handled by, well, Handles. A Handle would decide which block needs to be displayed and
where it needs to be displayed. Every page calls Handles, and each page calls unique and multiple Handles.

Handles are called when their URL's are accessed.



Middle
------

> What is a code pool in Magento?

In order to register a new module in Magento, developers tag files called codePool. Core, Community, and 3rd Party are available.


> What are the Session types available in Magento?

There are two types of sessions in Magento, customer and checkout. All customer related data is locked with customer sessions and all order and
quote data is stored within a checkout session. Session types are utilized separately because orders are placed, and checkout data must be
flushed. Thus, two types.

For example, a customer's first name is stored in `$_SESSION['customer']['first_name']`.


> What are the ways to optimize the Magento environment configuration?

* Cloud computing
* JS and CDSS should be merged into a single file whieh reduces load time
* CDN, multi-tenant architectures
* disable any unused modules
* never run everything on one server, microservices
* keep everything up to data
* dedicated microservices



Senior
------

> How do you achieve multi-level inheritance in Magento, PHP?

A module, is a logical group - a directory containing xml and php files (blocks, controllers, etc) related to a
specific functionality Using the modular approach implies that every module enacapsulates a feature and has minimum
dependencies on other modules


> How do you show a select number of products for guests in Magento?

#### Solution
```shell
app/code/core/Mage/Catalog/Block/Product/List/Toolbar.php
```
```php
public function setCollection($collection);

$limit = (int) $this->getLimit();
if ($limit) {
    $this->_collection->setPageSize($limit);
}

Mage::getSingleton('customer/session')->isLoggedIn();
```