# Section 2: Magento Architecture (22%)

[Previous Section](./1.md) | [Next Section](./3.md)
Magento Architecture
====================

Configuration System
--------------------

* One of Magento's core features is the ability to customize almost anything.
* Configuration is divided up into areas: global (base), frontend, adminhtml, webapi_rest, webapi_soap, and crontab
* Configuration is loaded depending on the area chosen
* Default behavior: global configuration is loaded, then specific area is merged (or loaded) on top of global configuration

Magento includes multiple XML files that cover a multitude of use cases during development. Module configuraton
is located in app/code/Vendor/Module/etc directory and usually contains these files:

1. module.xml - initialization or configuration of a module. contains the sequence element which determines load order
2. config.xml - where default configurations for the module are added
3. di.xml - where the apps dependency injection is configured. Virtual types, plugins, and argument modifications are set here too
4. acl.xml - where ACL nodes are configured and set
5. events.xml - where event observers are declared
6. [AREA]/routes.xml - where any controller routes are initialized
7. adminhtml/system.xml - any new store configuration fields are setup here

A core feature of Magento is that you can override almost any configuration file.

https://devdocs.magento.com/guides/v2.4/config-guide/config/config-create.html
https://devdocs.magento.com/guides/v2.4/config-guide/config/config-files.html
-----


## [Section 2: Magento Architecture (22%)](./2.md)  - 700

### **2.1** Demonstrate ability to design a Cloud solution

#### **What are the benefits and drawbacks of on-premise vs. Cloud? How do you move to Cloud? How does Cloud influence project development? What features are only available on Cloud? What are the differences between Starter and Pro plans?**

### **2.2** Demonstrate understanding of key concepts of Magento architecture

#### **Architecture in Magento 2 – What is it and how is it used in Magento Commerce?**

#### **What are the benefits and costs of database sharding? What is the Varnish Full Page Cache and why is it better than the built in FPC?**

#### **What are the basic responsibilities of templates and layouts in Magento 2? What are the basic steps for extending Magento 2 functionality with a code change or a third-party extension?**

#### **How can the site design be configured using the options found in the Admin UI under System > Design > Configuration?**

### **2.3** Demonstrate knowledge of how to use the Magento API for integrating with third-party systems

#### **What types of API does Magento Commerce have? What are the intended use cases for the different API types? What are the pros and cons of each type?**

#### **What methods of authentication do the Magento 2 APIs support?**

#### **Demonstrate the ability to manage credentials for the Magento API**

### **2.4** Demonstrate ability to design and administer websites, stores, store views

#### **What are use cases for product attributes scopes?**

#### **What is the effect of Website, Store, and Store View configuration scopes?**

#### **Understand display of product catalogs in websites, stores, and store views**

#### **Understand administration of websites, stores, and store views**

#### **Understand localization taxes and pricing in websites, stores, and store views**

### **2.5** Demonstrate understanding of the differences between Magento editions

#### **What are the main differences between Magento Open Source and Magento Commerce? What features are available only on Magento Commerce? (Commerce, Open Source, and B2B)**

#### **Differences between Magento 2 Commerce, Magento 2 Commerce Cloud, and Magento 2 Open Source**

#### **Advantages of Magento Commerce, Magento Commerce Cloud, Magento Open Source**

#### **Staging and previewing**

#### **Payment methods in Magento 2 Commerce**

#### **Customer attributes and segments in Magento 2 Commerce**

#### **Full page cache and indexing differences between editions**

#### **All other differences between Magento Open Source and Magento Commerce**

### **2.6** Demonstrate ability to identify infrastructure requirements for a Magento project

#### **What are the infrastructure elements of a typical Magento installation (database, search, CDN, cache, sessions, etc.)?**

### **2.7** Demonstrate ability to configure the Magento storefront functionality

#### **How are cookies used in Magento?**

#### **What must be done to configure cookies on multisite Magento implementations?**

#### **What is static content signing?**




## [Section 1: Magento Architecture (6%)](./1.md)  - 704

### **1.1**  Determine advanced uses of the Magento configuration system

#### **Understand how to create a custom config file. Demonstrate an understanding of the Magento Configuration files framework**

#### **Understand how to create a custom config file with validation, and a unique node that is overridden on merging**

#### **Understand how to create a config file with a remote schema**

### **1.2**  Demonstrate an ability to design complex customizations using plugins and di.xml

#### **Plugins sort order, plugin on plugin scenario, plugin debugging techniques. Demonstrate an understanding of virtual types, shared objects, object instantiation process, proxies, factories**

#### **How does an around plugin modify the plugin execution order?**

#### **How do you debug a plugin that is not executed?**

#### **Demonstrate Plugin on Plugin examples**

#### **Which classes are instantiated outside the ObjectManager, so they cannot be customizing using di.xml?**

#### **Demonstrate a use case for a virtual type (different instances of a class with a different set of arguments)**

### **1.3**  Demonstrate understanding of Magento events processing

#### **Demonstrate an understanding of the events processing flow. Influence of Staging on the event processing**

#### **What is a modification of the event processing mechanism introduced by the staging module?**

### **1.4**  Demonstrate an ability to use the Magento command-line interface

#### **Create a new CLI command, emulate different areas within it**

#### **Create a new CLI-command, configure it in `di.xml`, add optional/required options/keys**

#### **Environment specification using Area class**

#### **Environment emulation for a section of code**