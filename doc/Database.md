# Section 3: Working with Databases (14%)
Databases in Magento
====================

### Install/Upgrade Workflow

### Setup Scripts

Upgrade and install scripts are located in a modules setup folder.

[Previous Section](./2.md) | [Next Section](./4.md)

-----

## [Section 3: Working with Databases (14%)](./3.md) 704 Architect

### **3.1**  Demonstrate understanding of the architectural layers of the database access classes, including models, repositories, and data mappers

#### **Models, resource models, and collections in Magento, their impact on performance. Repositories, SearchCriteria, WebAPI, WebAPI access, extension attributes**

#### **How to create an entity that supports extension attributes**

#### **How to implement SearchCriteria processing in the `repository::getList` method**

#### **How to perform bulk save operations in Magento**

#### **How to extend the Magento data object (Data API class) with an attribute that has values in a remote system**

#### **How to extend existing WebAPI calls with a new parameter**

#### **How to create a dynamic WebAPI ACL**

#### **The difference between extension attributes and custom attributes**

### **3.2**  Demonstrate understanding of the staging workflow

#### **Staging modification to the Magento database operations (row_id, entity managers)**

#### **How does data versioning work?**

#### **Different possibilities of data versioning (row/table/database level) and how this is implemented in Magento**

#### **The role of the entity manager**

#### **High level staging implementation overview**

### **3.3**  Demonstrate an ability to use different types of setup scripts in Magento

#### **Schema and data setup scripts, uninstall scripts, recurring scripts, uninstall schema vs. uninstall data**

#### **What happens when an 'uninstall script' is executed: data version change, deleted tables, etc.**

#### **Recurring scripts and their order in the setup:upgrade process**

#### **Accessing areas and system configuration values in setup scripts**




## [Section 4: Using the Entity-Attribute-Value (EAV) Model (10%)](./4.md) 704 Architect

### **4.1**  Describe the EAV data access process in Magento

#### **Getting an attribute instance, impact of attribute sets, large number of attributes and attribute sets**

#### **What is the impact of 10,000 attribute sets? 1,000 attributes in a set?**

#### **How to get information about an attribute**

#### **How to perform attribute operations programmatically: assign it to a set/group, update properties, etc.**

### **4.2**  Describe the database tables for EAV entities and how to create them

#### **The EAV database structure, performance considerations, entity-level attribute properties (catalog_eav_attribute)**

#### **Where are catalog-specific attribute properties stored and what are they used for?**

#### **How does Magento store the attribute to attribute group association?**

#### **What backend types are available? How do you add a new backend type?**

#### **Specifics around static attributes**

### **4.3**  Demonstrate an ability to operate with attribute options

#### **Different ways to store attribute options. Using `eav_attribute_option_*` tables**

#### **Config base, database base options**

#### **The `eav_attribute_option_` table: tables that contain shared options between different entities, pros and cons of using the table**

### **4.4**  Demonstrate an ability to use non-catalog EAV entities

#### **Adding an attribute to Customer, Customer Address and Sales entities. Making an attribute visible in the Admin or the storefront. Pitfalls in attributes operations in non-catalog EAV attributes**

#### **Adding an attribute to customers, saving and loading the attribute, problems related to the save process. What is the role of attribute sets and groups for customer attributes?**

#### **Adding an attribute to customer addresses, the role of the ""is_system"" property and why it only works for the Customer Address entity**

#### **How to make a customer or customer address attribute visible in the My Account, Checkout, and Admin pages**

#### **What is the purpose of the SalesSetup class and why do you use the addAttribute method for sales entities?**
