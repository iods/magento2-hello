<h1 align="center">A Developer Guide</h1>
<br />
Some tips and tricks and help navigating various certifications.


Various guides and notes on architecture work for Magento.

* Solid product knowledge of Magento 2 Open Source and Magento 2 Commerce including systems functionality, basics of system architecture, an understanding of integration, and the most popular third-party modules included in the standard Magento 2 installation.
* Knowledge of basic ecommerce terms and a good understanding of typical business usage scenarios and trends.
* Basic understanding of networking, cloud, and server infrastructure.
* Basic understanding of the laws concerning privacy and online trading in the US and Europe, as well as other major trading nations.

This exam is for a senior Magento 2 developer/architect with 2 years of experience in customizing different areas of Magento Commerce, leading teams of Magento developers, leading projects, making key technical decisions on a Magento project, and working with customers to build project requirements.


This exam will validate the skills and knowledge needed to customize Magento in the following areas: core architecture, UI modifications, catalog, checkout, Magento Commerce features and security. The exam will also validate the ability to make architectural decisions, forecast the impact of a customization, and will test understanding of core mechanisms in the most important areas like price calculation for a product, checkout and quote operations.

## Magento Architecture

### Architect - 700

> Question One

### Architect - 704

> Question One


### 1.1 Determine advanced uses of the Magento configuration system
* Understand how to create a custom config file. Demonstrate an understanding of the Magento Configuration files framework
* Understand how to create a custom config file with validation and a unique node that is overridden on merging
* Understand how to create a config file with a remote schema
### 1.2 Demonstrate an ability to design complex customizations using plugins and di.xml
* Plugins sort order, plugin on plugin scenario, plugin debugging techniques. Demonstrate an understanding of virtual types, shared objects, object instantiation process, proxies, factories
* How does an around plugin modify the plugin execution order?
* How do you debug a plugin that is not executed?
* Demonstrate Plugin on Plugin examples
* Which classes are instantiated outside of the ObjectManager so they cannot be customizing using di.xml?
* Demonstrate a use case for a virtual type (different instances of a class with a different set of arguments)
  1.3 Demonstrate understanding of Magento events processing
  Demonstrate an understanding of the events processing flow. Influence of Staging on the event processing
  What is a modification of the event processing mechanism introduced by the staging module?
  1.4 Demonstrate an ability to use the Magento command-line interface
  Create a new CLI command, emulate different areas within it
  Create a new CLI-command, configure it in di.xml, add optional/required options/keys
  Environment specification using Area class
  Environment emulation for a section of code
  Section 2: Magento UI (7%)
  2.1 Demonstrate understanding UiComponents architecture
  UiComponent workflow, initialization, execution, configuration structure, data loading process
  Retrieving a UiCompnent's instance from the uiRegistry
  Understand the difference between executing a data provider component and loading data
  Describe the role of UiComponent PHP classes
  Understand the uiClass instance, extending uiComponent
  2.2 Demonstrate advanced use of Magento layouts
  Non-standard layouts, custom handles, debugging layouts
  Add a custom handle, obtain a list of handles loaded for a page
  Obtain the layout XML for a page
  Containers elements with a wrapping DIV tag
  Dynamically modify the layout tree
  2.3 Demonstrate an ability to operate with Magento blocks and templates
  Block caching, fallback debugging, email templates, translations
  Cache all instances of the block, specific instance
  Assign an object to the email template. Render different images depending on a locale in the email template
  Identify the location of block instantiation
  Print out all places where Magento looks for a template
  Demonstrate an understanding of different types of translations working together (inline, phrase in JavaScript code, CSV file)
  Section 3: Working with Databases (14%)
  3.1 Demonstrate understanding of the architectural layers of the database access classes, including models, repositories, and data mappers
  Models, resource models, and collections in Magento, their impact on performance. Repositories, SearchCriteria, WebAPI, WebAPI access, extension attributes
  How to create an entity that supports extension attributes
  How to implement SearchCriteria processing in the repository::getList method
  How to perform bulk save operations in Magento
  How to extend the Magento data object (Data API class) with an attribute that has values in a remote system
  How to extend exisitng WebAPI calls with a new parameter
  How to create a dynamic WebAPI ACL
  The difference between extension attributes and custom attributes
  3.2 Demonstrate understanding of the staging workflow
  Staging modification to the Magento database operations (row_id, entity managers)
  How does data versioning work?
  Different possibilities of data versioning (row/table/database level) and how this is implemented in Magento
  The role of the entity manager
  High level staging implementation overview
  3.3 Demonstrate an ability to use different types of setup scripts in Magento
  Schema and data setup scripts, uninstall scripts, recurring scripts, uninstall schema vs. uninstall data
  What happens when an uninstall script is executed: data version change, deleted tables, etc.
  Recurring scripts and their order in the setup:upgrade process
  Accessing areas and system configuration values in setup scripts
  Section 4: Using the Entity-Attribute-Value (EAV) Model (10%)
  4.1 Describe the EAV data access process in Magento
  Getting an attribute instance, impact of attribute sets, large number of attributes and attribute sets
  What is the impact of 10,000 attribute sets? 1,000 attributes in a set?
  How to get information about an attribute
  How to perform attribute operations programmatically: assign it to a set/group, update properties, etc.
  4.2 Describe the database tables for EAV entities and how to create them
  The EAV database structure, performance considerations, entity-level attribute properties (catalog_eav_attribute)
  Where are catalog-specific attribute properties stored and what are they used for?
  How does Magento store the attribute to attribute group association?
  What backend types are available? How do you add a new backend type?
  Specifics around static attributes
  4.3 Demonstrate an ability to operate with attribute options
  Different ways to store attribute options. Using eav_attribute_option_* tables
  Config base, database base options
  The eav_attribute_option_ table: tables that contain shared options between different entities, pros and cons of using the table
  4.4 Demonstrate an ability to use non-catalog EAV entities
  Adding an attribute to Customer, Customer Address and Sales entities. Making an attribute visible in the Admin or the storefront. Pitfalls in attributes operations in non-catalog EAV attributes
  Adding an attribute to customers, saving and loading the attribute, problems related to the save process. What is the role of attribute sets and groups for customer attributes?
  Adding an attribute to customer addresses, the role of the ""is_system"" property and why it only works for the Customer Address entity
  How to make a customer or customer address attribute visible in the My Account, Checkout, and Admin pages
  What is the purpose of the SalesSetup class and why do you use the addAttribute method for sales entities?
  Section 5: Developing with Adminhtml (5%)
  5.1 Demonstrate ability to use ACL
  Complex cases of ACL setup. WebAPI ACL, ACL process customization and debugging
  How to debug an ACL record
  How does a row-based ACL or IP-based ACL work in Magento?
  The connection between admin ACL and WebAPI ACL
  Different ways to access WebAPI resources including admin access
  5.2 Demonstrate understanding of the admin login process and admin actions processing
  Admin login, customizing and debugging issues related to admins logging into Magento, the Admin Action class
  Debugging the login process
  Logging in an admin user programmatically
  Customizing the login process: for example, adding 2-factor authentication
  Operations performed by the Magento\Backend\App\Action class, for example, the secret key
  5.3 Demonstrate an ability to create complex forms and grids
  Complex forms with custom elements and with tabs. Complex grids with custom columns and inline editing customizations
  Create custom elements for forms
  Create a form with tabs
  Create a form with a grid inside of a tab
  Forms for editing related/nested data
  Customization of inline editing in a grid; for example, a file uploader
  Bookmark filters selection for a grid
  Grid meta information: adding a new column that requires a join to another table
  Section 6: Customizing the Catalog (23%)
  6.1 Demonstrate an ability to understand and customize Magento products
  Selecting the right product type for a given requirement (configurable with custom options, bundle with grouped). Deciding to use non-standard products: for example, for licenses, subscriptions, courseware, or glasses. Product relations (related, upsells).
  Select a product type for a subscription/subscription bundled with a physical product
  Select a product type for courseware
  Select a product type for glasses with a prescription
  Compare custom options with configurable products
  Configurable product with custom options for the associated simple products
  Bundled product with custom options for its associated simple products
  What is the related products database structure? Understand the performance impact of having many related products
  Compare related with upsells
  Programmatically access related products, custom options, configurable parameters
  Dynamic related products
  6.2 Demonstrate an ability to perform complex operations with the Magento pricing framework
  Understand the pricing calculation and rendering framework. Which classes are involved in rendering/calculation? What is the role of indexing? How do different price modifiers work together?
  How is a price calculated on the product detail page, the product listing page? Price calculation classes. Relation to the price indexer
  The Magento\Framework\Price\* component and its extension in the Catalog module
  How to render a product price: which class to use, which data needs to be provided
  Indexed price vs. prices calculated on the fly
  Price configuration: tier prices, special price, custom option, configurable adjustment, catalog rules, cart rules
  How to change the price rendering process for a given product type/product instance
  How to add a custom price adjustment to modify the calculation process. What happens if the price index is not aligned with this change?
  6.3 Customize catalog price rules
  Programmatically create a catalog price rule, the impact of catalog price rules on performance, extending catalog price rule conditions with custom entities
  6.4 Determine how to use Magento categories
  Advanced category features: hierarchy, custom attributes, impact on performance
  What happens if a project has many categories?
  Dynamic rules for the order of products in category
  The category is_anchor attribute and its effect on performance
  6.5 Demonstrate an understanding of catalog indexers
  The indexing framework, the price indexer, the inventory indexer, the EAV indexer. How does Magento use indexed data?
  Estimate indexing customization efforts when making architectural decisions. Estimate indexing process complexity and time for different given conditions. The impact of indexing for frequent catalog updates.
  What steps does Magento perform when indexing? What is the role of the indexer_state table
  How to register a new indexer
  How does the price indexer work? Which events trigger it? How do different product types declare their indexers? How important is an order of indexers in price indexing?
  Inventory indexer overview, inventory indexing for different product types
  What is the scope of a price in the price index? How difficult is it to extend the scope of an index?
  Impact of many stores/websites on price indexing
  Custom price modifiers: Pros and cons of customizing the index versus adjusting the native features like price rules or custom options
  6.6 Demonstrate understanding of catalog staging and its impact on the system
  Flow modifications introduced by staging (triggers, row_id, data versions). Staging-related modifications of the indexing process
  Issues related to different row_id and entity_id
  Catalog triggers
  6.7 Demonstrate an understanding of the product search framework
  How to customize Elastic search
  6.8 Demonstrate understanding of importing products and categories in Magento
  Frequent imports, massive imports, import with many attributes
  Issues related to a frequent import, for example every minute
  Compare importing products using the native import, save by model, or custom SQL
  Specifics of importing a catalog with many attributes and attribute sets
  Importing categories and product relations
  Section 7: Customizing the Checkout Process (17%)
  7.1 Understand the Magento quote architecture and customizing quote-related functionality
  Quote-related objects, total models and the price calculation process, the add to cart process, custom add to cart operations, customizations of the price calculation, taxes and discount, various display settings
  The quote merge functionality
  Programmatically add a free gift when a certain condition is met
  Programmatically set a price for a product
  Taxes with discounts calculation
  The impact of many shopping cart price rules on performance
  Programmatically create shopping cart price rules
  Importing coupon codes
  Extend the shopping cart price rules with custom entities
  Programmatically separate line items in the shopping cart so there are two line items instead of one with qty=2
  Adding a new total model and evaluating its impact on taxes and discounts
  Shipping discounts behavior and customizations
  WebAPI for quote operations. Create a quote, add an item, create a coupon, add a discount
  7.2 Demonstrate an ability to customize and extend the checkout process
  Checkout steps, the REST API, customizations of the checkout API, the order placement process. The impact of many concurrent order placements
  Adding a step to the checkout after the payment step, or between the payment and shipping steps
  Implementing a ""one-click"" checkout, evaluate possible pitfalls such as discounts being applied or canceled when the order is placed
  The checkout REST API: Modifying the native flow (separate calls to save payment and to place the order)
  Extending the checkout REST API. Adding new parameters to different API endpoints. Using extension attributes
  Issues related to simultaneous order placement, inventory locking
  Determining the exact moment when the stock is decremented during an order placement
  Customizing the order placement such that it uses message queues
  Horizontal sharding of orders tables to improve order placement capacity. What challenges need to be resolved?
  7.3 Create and debug shipping and payment methods in Magento
  Different types of payment methods: gateway, offline, hosted. The gateway payment methods framework. The payment method availability logic. The shipping rates calculation process, debugging shipping rates and table rates customizations
  The gateway framework vs. AbstractMethod
  The structure of offline payment methods. What makes them "offline"?
  Partial invoices/refunds for payment methods
  Add a hosted-type payment method (redirects, custom order review page)
  Add a new shipping method. Customize the logic for getting a list of available shipping methods
  The shipping rate calculation flow. Debug shipping rates, identify plugins that that influence the shipping rate calculation process
  Customizing table rates. Add a new "column" to the "table", change the logic of selecting the rate.
  Gateway shipping methods. Remote call flow. How to avoid the remote call if it is unnecessary
  Section 8: Magento Commerce Features (13%)
  8.1 Demonstrate an ability to use message queues
  Create a listener/publisher. Use cases for using message queues
  How to register a listener/publisher for a queue
  How to configure a queue
  What is a use case to use message queues?
  8.2 Demonstrate understanding of customer segmentation
  Describe the customer segments functionality, its use cases, impact on performance, and programmatical operations with customer segments
  Programmatically create a customer segment
  Extend customer segments with new entities or attributes
  Understand the database structure of customer segments
  8.3 Demonstrate understanding of advanced capabilities in Magento Commerce
  Store credits, reward points, RMA, gift cards
  Compare RMA with refunds
  Customizing the RMA process
  Customizing store credits/reward points accrual/spending
  8.4 Demonstrate understanding of target rules
  Customer rules database structure, use cases, comparison to other product relations, operate with target rules programmatically
  Target rules vs. related products
  Extending target rules with a custom attribute or a custom entity
  Create a rule programmatically, understand the database structure of a rule
  What is the performance impact of having many target rules in the system?
  How does editing a product or adding new products affect existing target rules?
  Section 9: Understanding Magento Security (5%)
  9.1 Demonstrate understanding of frontend security with Magento
  Filter input and escape output; password and sensitive data hashing; validate user file uploads; how to prevent cross site scripting vulnerabilities
  How to validate field values before inserting them into the database
  How to escape output to remove HTML tags
  Using secure encryption and hashing functions to store sensitive values in the database
  Validate file uploads, the file type, the file contents, and the file metadata
  9.2 Demonstrate understanding Adminhtml security with Magento
  CSRF tokens; stored XSS; adminhtml secret key; security configuration; securing email from injection; preventing admin privilege escalation
  How to prevent CSRF attacks; the importance of the form_key field in forms
  How is the admin secret key generated in URLs?
  Security related admin configurations
  Security by obscurity, the custom admin path
  9.3 Demonstrate understanding of different types of attacks and preventing them with Magento
  Remote code execution; local and remote file inclusions; session hijacking; SQL injection; insecure functions; directory traversal attacks
  PHP functions that should never be used, per Magento recommendations (eval, serialize, etc.)
  How to prevent directory traversals attacks when uploading a file
  Importance of the HttpOnly property when setting a cookie
  Serving Magento from the base vs. the pub/ directory
  Retrieving the user IP from the REMOTE_ADDR header vs. the X-Forwarded-For header
  File operations influenced by user-submitted request parameters, how to stop directory traversal attacks and restrict access to dirs/files
  How to write secure SQL queries


### Order Management - 707

> Question One
- Some stuff to review



A modular system that function as standalone

Areas:
* Scope configuration allows Magento to load only required configuration files.
* Only the dependent configuration options for that area are loaded.
  an area may only have one component too, separate for each area if it works in both
* Typically areas have both behavior and view components
* Technically six areas, but you really only work with two (adminthml and frontend)

Increases efficiency by not loading everything on every request.

Each area can have different

Modular Code Structure - Framework is not modular
Theme -
Layout Files -
Merged Config Files -
Object Instantiation Magic -
Naming Convention for Controllers and Layouts -
Events and Plugins -

Configuration - app/etc (general system configuration)
Framework - vendor/magento/framework (magento framework classes)
Modules - vendor/magento/module-* (business logic)
Command Line Tool - bin/magento - important cli tool
Themes - app/design - contains static files belonging to a theme
Dev Tools - dev - framework, data installer
Generated - generate and contain all necessary classes, plugins, intercepters, etc.

For composer install of modules - vendor/magento/module-*
For repo of module - app/code/Magento/

For composer install of Framework - vendor/magento/framework
For repo install of framework - lib/internal/Magento/Framework/*

For composer install of themes - vendor/magento/themes-frontend
For repo install of themes - app/design/frontend & app/design/adminthml

Three configuration types:

Global config - app/etc
Module configuration - etc in module folder
Theme config - themes folders

CLasses in Magento

* Model/Resource and Model/Collection classes - Interact w/ databases and implement product or customer data, moving to api interfaces
* API Interfaces - internal api that defines what is available
* Controllers - Handles pages in the MVC
* Blocks - patterns representing a page. data containers for templates.
* Observers - m2 fires events during execution flow,
* Plugins - wrapper around things, modify behavior
* auxilliry classes to perform functions, like a
* Schema database ones
* UI Components - independent elements w/ own bakend parts
* Other - there are more

How do you get your class into the middle of the request flow?
1. adding class into array of constructor
2. a plugin
3. an observer

What is a module?
a module is a package of code that encapsulates a particular business feature or set of features.

A module, is a logical group - a directory containing xml and php files (blocks, controllers, etc) related to a specific functionality
Using the modular approach implies that every module enacapsulates a feature and has minimum dependencies on other modules

Naming a module, Vendor_Module,

When customizing  modules, 


# Exam Objectives and Scope

[Table of Contents](./) | [Next Section](./1.md)

-----


## [Section 1: Magento Architecture & Customization Techniques (33%)](./1.md)

### **1.1**  Describe the Magento module-based architecture

#### **Describe module architecture. What are the significant steps to add a new module? What are the different Composer package types? When would you place a module in the app/code folder versus another location?**

### **1.2**  Describe the Magento directory structure

#### **Describe the Magento directory structure. What are the naming conventions, and how are namespaces established? How can you identify the files responsible for some functionality?**

### **1.3**  Utilize configuration and configuration variables scope

#### **Determine how to use configuration files in Magento. Which configuration files are important in the development cycle?**

#### **Describe development in the context of website and store scopes. How do you identify the configuration scope for a given variable? How do native Magento scopes (for example, price or inventory) affect development and decision-making processes?**

#### **Demonstrate an ability to add different values for different scopes. How can you fetch a system configuration value programmatically? How can you override system configuration values for a given store using XML configuration?**

### **1.4**  Demonstrate how to use dependency injection (DI)

#### **Demonstrate the ability to use the dependency injection concept in Magento development. How are objects realized in code? Why is it important to have a centralized object creation process?**

#### **Identify how to use DI configuration files for customizing Magento. How can you override a native class, inject your class into another object, and use other techniques available in di.xml (for example, virtualTypes)?**

#### **Given a scenario, determine how to obtain an object using the ObjectManager object. How would you obtain a class instance from different places in the code?**

### **1.5**  Demonstrate ability to use plugins

#### **Demonstrate an understanding of plugins. How are plugins used in core code? How can they be used for customizations?**

### **1.6**  Configure event observers and scheduled jobs

#### **Demonstrate how to create a customization using an event observer. How are observers registered? How are they scoped for frontend or backend? How are automatic events created, and how should they be used? How are scheduled jobs configured?**

### **1.7**  Utilize the CLI

#### **Describe the usage of bin/magento commands in the development cycle. Which commands are available? How are commands used in the development cycle?**

### **1.8**  Describe how extensions are installed and configured

#### **How would you install and verify an extension by a customer’s request?**


## [Section 2: Request Flow Processing (7%)](./2.md)

### **2.1**  Describe how to use Magento modes

#### **Understand the pros and cons of using developer mode or production mode. How do you enable/disable maintenance mode?**

### **2.2**  Demonstrate the ability to create a frontend controller with different response types (HTML / JSON / redirect)

#### **How do you identify which module/controller corresponds to a given URL? What would you do to create a given URL?**

### **2.3**  Demonstrate how to use URL rewrites for a catalog product view to a different URL

#### **How is the user-friendly URL of a product or category defined? How can you change it? How do you determine which page corresponds to a given user-friendly URL?**


## [Section 3: Customizing the Magento UI (15%)](./3.md)

### **3.1**  Demonstrate the ability to customize the Magento UI using themes

#### **Demonstrate the ability to customize the Magento UI using themes. When would you create a new theme? How do you define theme hierarchy for a project?**

### **3.2**  Demonstrate an ability to create UI customizations using a combination of a block and template

#### **How do you assign a template to a block? How do you assign a different template to a native block?**

### **3.3**  Identify the uses of different types of blocks

#### **When would you use non-template block types?**

### **3.4**  Describe the elements of the Magento layout XML schema, including the major XML directives

#### **How do you use layout XML directives in your customizations? How do you register a new layout file?**

### **3.5**  Create and add code and markup to a given page

#### **How do you add new content to existing pages using layout XML?**


## [Section 4: Working with Databases in Magneto (18%)](./4.md)

### **4.1**  Describe the basic concepts of models, resource models, and collections

#### **What are the responsibilities of each of the ORM object types? How do they relate to one another?**

### **4.2**  Describe how entity load and save occurs

#### **How do you use the native Magento save/load process in the development process?**

### **4.3**  Describe how to filter, sort, and specify the selected values for collections and repositories

#### **How do you select a subset of records from the database?**

### **4.4**  Demonstrate an ability to use declarative schema

#### **How do you add a column using declarative schema? How do you modify a table added by another module? How do you delete a column? How do you add an index or foreign key using declarative schema? How do you manipulate data using data patches? What is the purpose of schema patches?**


## [Section 5: Developing with Adminhtml (11%)](./5.md)

### **5.1**  Create a controller for an admin router

#### **How would you create an admin controller? How do you ensure the right level of security for a new controller?**

### **5.2**  Define basic terms and elements of system configuration, including scopes, website, store, store view

#### **How would you add a new system configuration option? What is the difference in this process for different option types (secret, file)?**

### **5.3**  Define / identify basic terms and elements of ACL

#### **How would you add a new ACL resource to a new entity? How do you manage the existing ACL hierarchy?**

### **5.4**  Set up a menu item

#### **How do you add a new menu item to a given tab? How do you add a new tab to the Admin menu?**

### **5.5**  Create appropriate permissions for users

#### **How are menu items related to ACL permissions? How do you add a new user with given set of permissions?**


## [Section 6: Customizing Magento Business Logic (16%)](./6.md)

### **6.1**  Identify/describe standard product types (simple, configurable, bundled, etc.)

#### **How would you obtain a product of a specific type, and what tools (in general) does a product type model provide?**

### **6.2**  Describe category properties in Magento

#### **How do you create and manage categories?**

### **6.3**  Define how products are related to the category

#### **How do you assign and unassign products to categories?**

### **6.4**  Describe the difference in behavior of different product types in the cart

#### **How are configurable and bundle products rendered? How can you create a custom shopping cart renderer?**

### **6.5**  Describe native shipment functionality in Magento

#### **How do you customize the shipment step of order management?**

### **6.6**  Describe and customize operations available in the customer account area

#### **How would you add another tab in the “My Account” section? How do you customize the order history page?**

### **6.7**  Add or modify customer attributes

#### **How do you add or modify customer attributes in a setup script?**

### **6.8**  Customize the customer address

#### **How do you add another field to the customer address entity using a setup script?**



















## [Section 1: Magento Architecture & Customization Techniques (18%)](./1.md)

### **1.1**  Describe Magento’s module-based architecture

#### **Describe module limitations. How do different modules interact with each other? What side effects can come from this interaction?**

### **1.2**  Describe Magento’s directory structure

#### **Determine how to locate different types of files in Magento. Where are the files containing JavaScript, HTML, and PHP located? How do you find the files responsible for certain functionality?**

### **1.3**  Utilize configuration XML and variables scope

#### **Determine how to use configuration files in Magento. Which configuration files correspond to different features and functionality?**

### **1.4**  Demonstrate how to use dependency injection

#### **Describe Magento’s dependency injection approach and architecture. How are objects realized in Magento? Why is it important to have a centralized process creating object instances?**

#### **Identify how to use DI configuration files for customizing Magento. How can you override a native class, inject your class into another object, and use other techniques available in di.xml (such as virtualTypes)?**

### **1.5**  Demonstrate ability to use plugins

#### **Demonstrate how to design complex solutions using the plugin’s life cycle. How do multiple plugins interact, and how can their execution order be controlled? How do you debug a plugin if it doesn’t work?**

#### **Identify strengths and weaknesses of plugins. What are the limitations of using plugins for customization? In which cases should plugins be avoided?**

### **1.6**  Configure event observers and scheduled jobs

#### **Demonstrate how to configure observers. How do you make your observer only be active on the frontend or backend?**

#### **Demonstrate how to configure a scheduled job. Which parameters are used in configuration, and how can configuration interact with server configuration?**

#### **Identify the function and proper use of automatically available events, for example *_load_after, etc.**

### **1.7**  Utilize the CLI

#### **Describe the usage of bin/magento commands in the development cycle. Which commands are available? How are commands used in the development cycle?**

#### **Demonstrate an ability to create a deployment process. How does the application behave in different deployment modes, and how do these behaviors impact the deployment approach for PHP code, frontend assets, etc.?**

### **1.8**  Demonstrate the ability to manage the cache

#### **Describe cache types and the tools used to manage caches. How do you add dynamic content to pages served from the full page cache?**

#### **Describe how to operate with cache clearing. How would you clean the cache? In which case would you refresh cache/flash cache storage?**

#### **Describe how to clear the cache programmatically. What mechanisms are available for clearing all or part of the cache?**


## [Section 2: Request Flow Processing (12%)](./2.md)

### **2.1**  Utilize modes and application initialization

#### **Identify the steps for application initialization. How would you design a customization that should act on every request and capture output data regardless of the controller?**

#### **Describe how to use Magento modes. What are pros and cons of using developer mode/production mode? When do you use default mode? How do you enable/disable maintenance mode?**

#### **Describe front controller responsibilities. In which situations will the front controller be involved in execution, and how can it be used in the scope of customizations?**

### **2.2**  Demonstrate ability to process URLs in Magento

#### **Describe how Magento processes a given URL. How do you identify which module and controller corresponds to a given URL? What is necessary to create a custom URL structure?**

#### **Describe the URL rewrite process and its role in creating user-friendly URLs. How are user-friendly URLs established, and how are they customized?**

#### **Describe how action controllers and results function. How do controllers interact with another? How are different response types generated?**

### **2.3**  Demonstrate ability to customize request routing

#### **Describe request routing and flow in Magento. When is it necessary to create a new router or to customize existing routers? How do you handle custom 404 pages?**

### **2.4**  Determine the layout initialization process

#### **Determine how layout is compiled. How would you debug your layout.xml files and verify that the right layout instructions are used?**

#### **Determine how HTML output is rendered. How does Magento flush output, and what mechanisms exist to access and customize output?**

#### **Determine module layout XML schema. How do you add new elements to the pages introduced by a given module?**

#### **Demonstrate the ability to use layout fallback for customizations and debugging. How do you identify which exact layout.xml file is processed in a given scope? How does Magento treat layout XML files with the same names in different modules?**

#### **Identify the differences between admin and frontend scopes. What differences exist for layout initialization for the admin scope?**

### **2.5**  Determine the structure of block templates

#### **Identify and understand root templates, empty.xml, and page_layout. How are page structures defined, including number of columns, which basic containers are present, etc.?**

#### **Describe the role of blocks and templates in the request flow. In which situations would you create a new block or a new template?**


## [Section 3: Customizing the Magento UI (10%)](./3.md)

### **3.1**  Demonstrate ability to utilize themes and the template structure

#### **Demonstrate the ability to customize the Magento UI using themes. When would you create a new theme? How do you define theme hierarchy for your project?**

#### **Demonstrate the ability to customize/debug templates using the template fallback process. How do you identify which exact theme file is used in different situations? How can you override native files?**

### **3.2**  Determine how to use blocks

#### **Demonstrate an understanding of block architecture and its use in development. Which objects are accessible from the block? What is the typical block’s role?**

#### **Identify the stages in the lifecycle of a block. In what cases would you put your code in the _prepareLayout(), _beforeToHtml(), and _toHtml() methods? How would you use events fired in the abstract block?**

#### **Describe how blocks are rendered and cached.**

#### **Identify the uses of different types of blocks. When would you use non-template block types? In what situation should you use a template block or other block types?**

### **3.3**  Demonstrate ability to use layout and XML schema

#### **Describe the elements of the Magento layout XML schema, including the major XML directives. How do you use layout XML directives in your customizations?**

#### **Describe how to create a new layout XML file.**

#### **Describe how to pass variables from layout to block.**

### **3.4**  Utilize JavaScript in Magento

#### **Describe different types and uses of JavaScript modules. Which JavaScript modules are suited for which tasks?**

#### **Describe UI components. In which situation would you use UiComponent versus a regular JavaScript module?**

#### **Describe the use of requirejs-config.js, x-magento-init, and data-mage-init.**


## [Section 4: Working with Databases in Magento (7%)](./4.md)

### **4.1**  Demonstrate ability to use data-related classes

#### **Describe repositories and data API classes. How do you obtain an object or set of objects from the database using a repository? How do you configure and create a SearchCriteria instance using the builder? How do you use Data/Api classes?**

#### **Describe how to create and register new entities. How do you add a new table to the database?**

#### **Describe the entity load and save process.**

#### **Describe how to extend existing entities. What mechanisms are available to extend existing classes, for example by adding a new attribute, a new field in the database, or a new related entity?**

#### **Describe how to filter, sort, and specify the selected values for collections and repositories. How do you select a subset of records from the database?**

#### **Describe the database abstraction layer for Magento. What type of exceptions does the database layer throw? What additional functionality does Magento provide over Zend_Adapter?**

### **4.2**  Demonstrate an ability to use declarative schema

#### **Demonstrate use of schema. How to manipulate columns and keys using declarative schema? What is the purpose of whitelisting? How to use Data and Schema patches? How to manage dependencies between patch files?**


## [Section 5: using the Entity-Attribute-Value (EAV) Model (8%)](./5.md)

### **5.1**  Demonstrate ability to use EAV model concepts

#### **Describe the EAV hierarchy structure. What happens when a new attribute is added to the system? What is the role of attribute sets and attribute groups? How are attributes presented in the admin?**

#### **Describe how EAV data storage works in Magento. Which additional options do you have when saving EAV entities? How do you create customizations based on changes to attribute values?**

#### **Describe the key differences between EAV and flat table collections. In which situations would you use EAV for a new entity? What are the pros and cons of EAV architecture?**

### **5.2**  Demonstrate ability to use EAV entity load and save


#### **Describe the EAV load and save process and differences from the flat table load and save process. What happens when an EAV entity has too many attributes? How does the number of websites/stores affect the EAV load/save process? How would you customize the load and save process for an EAV entity in the situations described here?**

### **5.3**  Demonstrate ability to manage attributes


#### **Describe EAV attributes, including the frontend/source/backend structure. How would you add dropdown/multiselect attributes? What other possibilities do you have when adding an attribute (to a product, for example)?**

#### **Describe how to implement the interface for attribute frontend models. What is the purpose of this interface? How can you render your attribute value on the frontend?**

#### **Identify the purpose and describe how to implement the interface for attribute source models. For a given dropdown/multiselect attribute, how can you specify and manipulate its list of options?**

#### **Identify the purpose and describe how to implement the interface for attribute backend models. How (and why) would you create a backend model for an attribute?**

#### **Describe how to create and customize attributes. How would you add a new attribute to the product, category, or customer entities? What is the difference between adding a new attribute and modifying an existing one?**


## [Section 6: Developing with Adminhtml (10%)](./6.md)

### **6.1**  Describe common structure/architecture

#### **Describe the difference between Adminhtml and frontend. What additional tools and requirements exist in the admin?**

### **6.2**  Define form and grid widgets


#### **Define form structure, form templates, grids, grid containers, and elements. What steps are needed to display a grid or form?**

#### **Describe the grid and form workflow. How is data provided to the grid or form? How can this be process be customized or extended?**

#### **Describe how to create a simple form and grid for a custom entity. Given a specific entity with different types of fields (text, dropdown, image, file, date, and so on) how would you create a grid and a form?**

### **6.3**  Define system configuration XML and configuration scope


#### **Define basic terms and elements of system configuration XML, including scopes. How would you add a new system configuration option? What is the difference in this process for different option types (secret, file)?**

#### **Describe system configuration data retrieval. How do you access system configuration options programmatically?**

### **6.4**  Utilize ACL to set menu items and permissions


#### **Describe how to set up a menu item and permissions. How would you add a new menu item in a given tab? How would you add a new tab in the Admin menu? How do menu items relate to ACL permissions?**

#### **Describe how to check for permissions in the permissions management tree structures. How would you add a new user with a given set of permissions? How can you do that programmatically?**


## [Section 7: Customizing the Catalog (12%)](./7.md)

### **7.1**  Demonstrate ability to use products and product types


#### **Identify/describe standard product types (simple, configurable, bundled, etc.). How would you obtain a product of a specific type? What tools (in general) does a product type model provide? What additional functionality is available for each of the different product types?**

### **7.2**  Describe price functionality


#### **Identify the basic concepts of price generation in Magento. How would you identify what is composing the final price of the product? How can you customize the price calculation process?**

#### **Describe how price is rendered in Magento. How would you render price in a given place on the page, and how would you modify how the price is rendered?**

### **7.3**  Demonstrate ability to use and customize categories

#### **Describe category properties and features. How do you create and manage categories?**

#### **Describe the category hierarchy tree structure implementation (the internal structure inside the database). What is the meaning of parent_id 0? How are paths constructed? Which attribute values are required to display a new category in the store? What kind of strategies can you suggest for organizing products into categories?**

### **7.4**  Determine and manage catalog rules


#### **Identify how to implement catalog price rules. When would you use catalog price rules? How do they impact performance? How would you debug problems with catalog price rules?**


## [Section 8: Customizing the Checkout Process (13%)](./8.md)

### **8.1**  Demonstrate ability to use quote, quote item, address, and shopping cart rules in checkout


#### **Describe how to modify these models and effectively use them in customizations.**

#### **Describe how to customize the process of adding a product to the cart. Which different scenarios should you take into account?**

### **8.2**  Demonstrate ability to use totals models


#### **Describe how to modify the price calculation process in the shopping cart. How can you add a custom totals model or modify existing totals models?**

### **8.3**  Demonstrate ability to customize the shopping cart


#### **Describe how to implement shopping cart rules. What is the difference between sales rules and catalog rules? How do sales rules affect performance? What are the limitations of the native sales rules engine?**

#### **Describe add-to-cart logic in different scenarios. What is the difference in adding a product to the cart from the product page, from the wishlist, by clicking Reorder, and during quotes merge?**

#### **Describe the difference in behavior of different product types in the shopping cart. How are configurable and bundle products rendered? How can you create a custom shopping cart renderer?**

#### **Describe the available shopping cart operations. Which operations are available to the customer on the cart page? How can you customize cart edit functionality? How would you create an extension that deletes one item if another was deleted? How do you add a field to the shipping address?**

### **8.4**  Demonstrate ability to customize shipping and payment methods

#### **Describe shipping methods architecture. How can you create a new shipping method? What is the relationship between carriers and rates?**

#### **Describe how to troubleshoot shipping methods and rate results. Where do shipping rates come from? How can you debug the wrong shipping rate being returned?**

#### **Describe how to troubleshoot payment methods. What types of payment methods exist? What are the different payment flows?**


## [Section 9: Sales Operations (5%)](./9.md)

### **9.1**  Demonstrate ability to customize sales operations

#### **Describe how to modify order processing and integrate it with a third-party ERP system.**

#### **Describe how to modify order processing flow. How would you add new states and statuses for an order? How do you change the behavior of existing states and statuses?**

#### **Described how to customize invoices. How would you customize invoice generation, capturing, and management?**

#### **Describe refund functionality in Magento. Which refund types are available, and how are they used?**


## [Section 10: Customer Management (5%)](./10.md)

### **10.1**  Demonstrate ability to customize My Account

#### **Describe how to customize the “My Account” section. How do you add a menu item? How would you customize the “Order History” page?**

### **10.2**  Demonstrate ability to customize customer functionality

#### **Describe how to add or modify customer attributes.**

#### **Describe how to extend the customer entity. How would you extend the customer entity using the extension attributes mechanism?**

#### **Describe how to customize the customer address. How would you add another field into the customer address?**

#### **Describe customer groups and their role in different business processes. What is the role of customer groups? What functionality do they affect?**

#### **Describe Magento functionality related to VAT. How do you customize VAT functionality?**