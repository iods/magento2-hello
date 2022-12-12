<h1 align="center">Module Guide</h1>
<br />



### Remove all static

```shell
rm -rf pub/static/*
```

### Debugging Knockout

Debugging
```html
<div data-bind="text: ko.computed(function() { debugger; })"></div>
```

Print Data
```html
<div data-bind="text: ko.toJSON(method.method_code)"></div>
```

# Writing Magento Modules

All custom modules should have a **Namespace** and **Module Name**.
These are used below as `{Namespace}` and `{Module}`.

> **Caution:** The Magento autoloader is known to have problems with CamelCase namespaces and/or modules between Windows and *nix systems. If your module requires more than one word for either of these, it is best to just concatenate them to avoid any issues (Example: `{Namespace}_{Examplemodule}`).

## Index

* [Directory Structure](#directory_structure)
* [Setup](#setup)
    * [Tell Magento how to load your module](#step1)
    * [Create your module's configuration](#step2)
    * [Create your module's administration settings](#step3) (optional)
* [Write your module classes](#classes)
    * [Blocks](#blocks)
    * [Controllers](#controllers)
        * [Frontend](#frontend)
        * [Backend (Admin)](#backend)
    * [Helpers](#helpers)
    * [Models](#models)
        * [Data Models](#data)
        * [Resource Models](#resource)
        * [Observers](#observers)
* [Extending Magento classes](#extending)
* [Tips](#tips)

<a name="directory_structure"></a>
## Standard Directory Structure

> **Note:** Not all paths are required (`app/design`, `skin`), only implement the ones you need.

```python
+-app
| +-code
| | +-local
| |   +-{Namespace}
| |     +-{Module}
| |       +-Block
| |       | +-Adminhtml
| |       +-controllers
| |       | +-Adminhtml
| |       | | +-{ControllerName}Controller.php  # Backend controller
| |       | +-{ControllerName}Controller.php    # Frontend controller
| |       +-etc
| |       | +-adminhtml.xml  # Admin ACL and other settings
| |       | +-config.xml     # Configuration settings for your module
| |       | +-system.xml     # Administration settings and form options
| |       +-Helper
| |       | +-Data.php
| |       +-Model
| |       | +-Resource
| |       | | +-{EntityName}
| |       | | |  +-Collection.php  # Collection model for {entity}
| |       | | +-{EntityName}.php   # Resource model for {entity}
| |       | +-Observer.php         # Used for subscribing to Magento events
| |       | +-{EntityName}.php     # Data model for {entity}
| |       +-sql
| |       | +-{namespace}_{module}_setup
| |       |   +-mysql4-install-{X}.{X}.{X}.php
| |       |   +-mysql4-upgrade-{X}.{X}.{X}-{X}.{X}.{X}.php
| |       +-Test
| +-design
| | +-adminhtml
| | | +-default
| | |   +-default
| | |     +-layout
| | |     | +-{namespace}
| | |     |   +-{module}.xml
| | |     +-template
| | |       +-{namespace}
| | |         +-{module}
| | +-frontend
| |   +-base
| |     +-default
| |       +-layout
| |       | +-{namespace}
| |       |   +-{module}.xml
| |       +-template
| |         +-{namespace}
| |           +-{module}
| +-etc
|   +-modules
|     +-{Namespace}_{Module}.xml
+-skin
  +-adminhtml
  | +-default
  |   +-default
  |     +-css
  |     | +-{namespace}
  |     |   +-{module}
  |     +-images
  |     | +-{namespace}
  |     |   +-{module}
  |     +-js
  |       +-{namespace}
  |         +-{module}
  +-frontend
    +-base
      +-default
        +-css
        | +-{namespace}
        |   +-{module}
        +-images
        | +-{namespace}
        |   +-{module}
        +-js
          +-{namespace}
            +-{module}
```

<a name="setup"></a>
## Setup

<a name="step1"></a>
### 1. Tell Magento how to load your module

Magento needs to know that it should load your module and where to find it. For this, create an XML file under `app/etc/modules/{Namespace}_{Module}.xml`:

```xml
<?xml version="1.0"?>
<config>
    <modules>
        <{Namespace}_{Example}>
            <active>true</active>
            <codePool>local</codePool>
            <!-- Remove this section if your module does not depend on other Magento modules -->
            <depends>
                <Mage_Core/>
            </depends>
        </{Namespace}_{Example}>
    </modules>
</config>
```

The `<depends>` block above is for illustrative purposes only. If your module requires others to be loaded before it, list them under `<depends>` - otherwise you can remove it or replace it with an empty node (`<depends/>`).

<a name="step2"></a>
### 2. Create your module's configuration

Create your module's `config.xml` under `app/code/local/{Namespace}/{Module}/etc`. Again, not all sections are required and it will greatly depend on your module and what it needs - however, this example covers the most common use cases:

```xml
<?xml version="1.0"?>
<config>
    <modules>
        <{Namespace}_{Example}>
            <version>{X}.{X}.{X}</version>
        </{Namespace}_{Example}>
    </modules>
    <global>
        <blocks>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Block</class>
            </{namespace}_{module}>
        </blocks>
        <helpers>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Helper</class>
            </{namespace}_{module}>
        </helpers>
        <models>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Model</class>
                <resourceModel>{namespace}_{module}_resource</resourceModel>
            </{namespace}_{module}>
            <{namespace}_{module}_resource>
                <class>{Namespace}_{Example}_Model_Resource</class>
                <!-- Remove this section if your module does not require any custom database tables -->
                <entities>
                    <{entity_name}}><table>{namespace}_{module}_{table_name}</table></{entity_name}>
                </entities>
            </{namespace}_{module}_resource>
        </models>
        <resources>
            <{namespace}_{module}_setup>
                <setup>
                    <module>{Namespace}_{Example}</module>
                </setup>
                <connection>
                    <use>core_setup</use>
                </connection>
            </{namespace}_{module}_setup>
            <{namespace}_{module}_write>
                <connection>
                    <use>core_write</use>
                </connection>
            </{namespace}_{module}_write>
            <{namespace}_{module}_read>
                <connection>
                    <use>core_read</use>
                </connection>
            </{namespace}_{module}_read>
        </resources>
        <!-- Remove this section if your module does not require any event observers -->
        <events>
            <{event_name}>
                <observers>
                    <{namespace}_{module}_{event_name}>
                        <type>model</type>
                        <class>{namespace}_{module}/observer</class>
                        <method>{methodName}</method>
                    </{namespace}_{module}_{event_name}>
                </observers>
            </{event_name}>
        </events>
    </global>
    <admin>
         <!-- Remove this section if your module does not have any admin controllers -->
         <routers>
            <adminhtml>
                <args>
                    <modules>
                        <{namespace}_{module} before="Mage_Adminhtml">{Namespace}_{Example}_Adminhtml</{namespace}_{module}>
                    </modules>
                </args>
            </adminhtml>
        </routers>
    </admin>
    <adminhtml>
        <!-- Remove this section if your module does not require admin layout updates -->
        <layout>
            <updates>
                <{namespace}_{module}>
                    <file>{namespace}/{module}.xml</file>
                </{namespace}_{module}>
            </updates>
        </layout>
    </adminhtml>
    <frontend>
        <!-- Remove this section if your module does not have any frontend controllers -->
        <routers>
            <{namespace}_{module}>
                <use>standard</use>
                <args>
                    <module>{Namespace}_{Example}</module>
                    <frontName>{namespace}</frontName>
                </args>
            </{namespace}_{module}>
        </routers>
        <!-- Remove this section if your module does not require frontend layout updates -->
        <layout>
            <updates>
                <{namespace}_{module}>
                    <file>{namespace}/{module}.xml</file>
                </{namespace}_{module}>
            </updates>
        </layout>
    </frontend>
    <!-- Remove this section if your module does not have system configuration -->
    <default>
        <{namespace}_{module}>
            <{group_name}>
                <enabled>0</enabled>
                <debug>0</debug>
            </{group_name}>
        </{namespace}_{module}>
    </default>
    <!-- Remove this section if your module does not require a cron task -->
    <crontab>
        <jobs>
            <{namespace}_{module}_{job_name}>
                <schedule><cron_expr>* * * * *</cron_expr></schedule>
                <run><model>{namespace}_{module}/observer::{methodName}</model></run>
            </{namespace}_{module}_{job_name}>
        </jobs>
    </crontab>
</config>
```

The comments above should explain which sections can be removed if your module does not require/need them.

> **Note:** Be sure to replace `{X}.{X}.{X}` with your module's version number (Example: `1.0.0`). This number is stored in the database table `core_resource` and is also used for running module setup scripts under `app/code/local/{Namespace}/{Module}/sql/{namespace}_{module}_setup`.

<a name="step3"></a>
### 3. Create your module's administration settings (optional)

Create the file `system.xml` under `app/code/local/{Namespace}/{Module}/etc`. Within this file you can define custom admin configuration tabs, admin settings, etc. Two example settings are included below (`enabled` and `debug`) which provide simple on/off settings in the Magento administration interface.

```xml
<?xml version="1.0"?>
<config>
    <tabs>
        <{namespace}_{module} translate="label" module="{namespace}_{module}">
            <label>{Namespace}</label>
            <sort_order>300</sort_order>
        </{namespace}_{module}>
    </tabs>
    <sections>
        <{namespace}_{module} translate="label" module="{namespace}_{module}">
            <label>{Section Label Text}</label>
            <tab>{namespace}_{module}</tab>
            <sort_order>1</sort_order>
            <show_in_default>1</show_in_default>
            <show_in_website>1</show_in_website>
            <show_in_store>1</show_in_store>
            <groups>
                <{group_name} translate="label">
                    <label>{Group Label Text}</label>
                    <sort_order>1</sort_order>
                    <show_in_default>1</show_in_default>
                    <show_in_website>1</show_in_website>
                    <show_in_store>1</show_in_store>
                    <fields>
                        <enabled translate="label">
                            <label>Enable Module</label>
                            <frontend_type>select</frontend_type>
                            <source_model>adminhtml/system_config_source_yesno</source_model>
                            <sort_order>1</sort_order>
                            <show_in_default>1</show_in_default>
                            <show_in_website>0</show_in_website>
                            <show_in_store>0</show_in_store>
                        </enabled>
                        <debug translate="label">
                            <depends><enabled>1</enabled></depends>
                            <label>Debug</label>
                            <frontend_type>select</frontend_type>
                            <source_model>adminhtml/system_config_source_enabledisable</source_model>
                            <sort_order>2</sort_order>
                            <show_in_default>1</show_in_default>
                            <show_in_website>0</show_in_website>
                            <show_in_store>0</show_in_store>
                        </debug>
                    </fields>
                </{group_name}>
            </groups>
        </{namespace}_{module}>
    </sections>
</config>
```

> **Note:** Each setting relates to the `<default>` key in `config.xml` - which specifies that setting's default value.

In order for the settings to show up/work - you must also create ACL rules for your new admin config section. For that, we need to create `adminhtml.xml` under `app/code/local/{Namespace}/{Module}/etc`.

```xml
<?xml version="1.0"?>
<config>
    <acl>
        <resources>
            <admin>
                <children>
                    <system>
                        <children>
                            <config>
                                <children>
                                    <{namespace}_{module] translate="title" module="{namespace}_{module]">
                                        <title>{Namespace} {Module}</title>
                                        <sort_order>1</sort_order>
                                    </{namespace}_{module]>
                                </children>
                            </config>
                        </children>
                    </system>
                </children>
            </admin>
        </resources>
    </acl>
</config>
```

> **Note:** For older Magento versions, it is necessary to also specify the above `<acl>` area under the `<adminhtml>` section of `config.xml`.

<a name="classes"></a>
## Write your module classes

<a name="blocks"></a>
### Blocks

Blocks control the HTML output of a specific section/area of various pages within Magento. You can create your own blocks but the most common use is to extend another Magento block.

```php
<?php

class {Namespace}_{Module}_Block_{BlockName} extends Mage_Core_Block_Template // For Adminhtml, extend: Mage_Adminhtml_Block_Abstract
{

}
```

<a name="controllers"></a>
### Controllers

Controllers are broken into 2 types: [frontend](#frontend) and [backend](#backend) (admin). The difference requires extending different base Magento classes.

<a name="frontend"></a>
#### Frontend

```php
<?php

class {Namespace}_{Module}_{ControllerName}Controller extends Mage_Core_Controller_Front_Action
{
    /**
     * Maps to: /{namespace}/{controllerName}/{actionName}/
     */
    public function {actionName}Action()
    {
        // Example of retrieving a query parameter
        $queryParameter = $this->getRequest()->getParam('query_parameter', 'Default Value (if not present)');

        // Example of getting a URL from the router
        $url = Mage::app()->getStore()->getUrl('{module}/{controller}');

        // Example of performing a redirect
        $this->_redirectUrl($url);
    }
}
```

<a name="backend"></a>
#### Backend (Admin)

```php
<?php

class {Namespace}_{Module}_Adminhtml_{ControllerName}Controller extends Mage_Adminhtml_Controller_Action
{
    protected function _initAction()
    {
        $this->loadLayout()
            ->_setActiveMenu('{menu_name}')
            ->_addBreadcrumb(
                '{Breadcrumb Text}',
                '{Breadcrumb Text}',
                // ...
            );
        return $this;
    }

    public function {actionName}Action()
    {
        $this->_title('{Title Text}');
        $this->_initAction()->renderLayout();

        // Example of adding a success notice message
        Mage::getSingleton('adminhtml/session')->addSuccess('{Success Message Text}');

        // Example of adding an error notice message
        Mage::getSingleton('adminhtml/session')->addError('{Error Message Text}');
    }
}
```

<a name="helpers"></a>
### Helpers

You must create one Helper class, however - it can remain empty. These classes are used for general functions/methods that are required between different class types (Example: retrieving configuration values).

```php
<?php

class {Namespace}_{Example}_Helper_Data extends Mage_Core_Helper_Abstract
{
}
```

> **Note:** This class can then be retrieved with: `Mage::helper('{namespace}_{module}')`

<a name="models"></a>
### Models

Models can be broken into 2 types: [data models](#data) and [resource models](#resource). Resource models control the interaction with the database (MySQL) whereas data models can range in responsibilities but usually manipulate data between controllers and resource models.

<a name="data"></a>
#### Data Model

```php
<?php

class {Namespace}_{Module}_Model_{EntityName} extends Mage_Core_Model_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}');
    }
}
```

> **Note:** This class can then be retrieved with: `Mage::getModel('{namespace}_{module}/{entity_name}')`

<a name="resource"></a>
#### Resource Model

```php
<?php

class {Namespace}_{Module}_Model_Resource_{EntityName} extends Mage_Core_Model_Mysql4_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}', '{primary_key}');
    }
}
```

> **Note:** This class can then be retrieved with: `Mage::getResourceModel('{namespace}_{module}/{entity_name}')` However, it is common practice to retrieve it from the data model instance: `Mage::getModel('{namespace}_{module}/{entity_name}')->getResource()`

You can also (optionally) define the Collection class used. The Collection is used to handle many instances of your resource models (saving many rows, retrieving many rows, iterating, etc.).

```php
<?php

class {Namespace}_{Module}_Model_Resource_{EntityName}_Collection extends Mage_Core_Model_Mysql4_Collection_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}');
    }
}
```

> **Note:** This class can then be retrieved from the data modal instance with: `Mage::getModel('{namespace}_{module}/{entity_name}')->getCollection()`

<a name="observers"></a>
#### Observers

The easiest and most flexible way of extending Magento features is by listening and responding to events with an observer class. Which events your module listens for is defined in your module's `config.xml`.

```php
<?php

class {Namespace}_{Module}_Model_Observer
{
    public function {methodName}(Varien_Event_Observer $observer)
    {
        return $this;
    }
}
```

<a name="extending"></a>
## Extending Magento classes

Extending a Magento (or other module) class is relatively easy. For blocks, helpers, models, and resource models just use the following syntax in your module's `config.xml` (under `<blocks>`, `<models>`, etc.) to rewrite a Magento class to yours:

```xml
            <{module_to_override}>
                <rewrite>
                    <{class_to_override}>{Namespace}_{Module}_Block_{ClassToOverride}</{class_to_override}>
                </rewrite>
            </{module_to_override}>
```

Here is an example of rewriting `Mage_Core_Model_Email_Template` with `Acme_Custom_Model_Email_Template`:

```xml
<?xml version="1.0"?>
<config>
    <global>
        <models>
            <core>
                <rewrite>
                    <email_template>Acme_Custom_Model_Email_Message</email_template>
                </rewrite>
            </core>
        </models>
    </global>
</config>
```

> **Caution:** It is important to remember that core Magento modules (those namespaced with `Mage_`) do not require the use of `mage_`. So the example above uses just `core` rather than `mage_core`.

<a name="tips"></a>
## Tips

#### `var_dump()` and Magento

Trying to `var_dump()` a Magento class instance will quickly lead to headaches because of circular references. Most Magento classes extend `Varien_Object` and thus expose a `debug()` method which is much better for dumping:

```php
<?php

var_dump($object->debug());
```

#### Logging

The easiest way to write to the system logger (or your own custom log file) is to use the `log()` method exposed by the `Mage` class:

```php
<?php

Mage::log('{Log Message Text}', (int) '{(optional) Log Level}', '{(optional) Log Filename}', (bool) '{(optional) Force Writing}');
```# Writing Magento Modules

All custom modules should have a **Namespace** and **Module Name**.
These are used below as `{Namespace}` and `{Module}`.

> **Caution:** The Magento autoloader is known to have problems with CamelCase namespaces and/or modules between Windows and *nix systems. If your module requires more than one word for either of these, it is best to just concatenate them to avoid any issues (Example: `{Namespace}_{Examplemodule}`).

## Index

* [Directory Structure](#directory_structure)
* [Setup](#setup)
    * [Tell Magento how to load your module](#step1)
    * [Create your module's configuration](#step2)
    * [Create your module's administration settings](#step3) (optional)
* [Write your module classes](#classes)
    * [Blocks](#blocks)
    * [Controllers](#controllers)
        * [Frontend](#frontend)
        * [Backend (Admin)](#backend)
    * [Helpers](#helpers)
    * [Models](#models)
        * [Data Models](#data)
        * [Resource Models](#resource)
        * [Observers](#observers)
* [Extending Magento classes](#extending)
* [Tips](#tips)

<a name="directory_structure"></a>
## Standard Directory Structure

> **Note:** Not all paths are required (`app/design`, `skin`), only implement the ones you need.

```python
+-app
| +-code
| | +-local
| |   +-{Namespace}
| |     +-{Module}
| |       +-Block
| |       | +-Adminhtml
| |       +-controllers
| |       | +-Adminhtml
| |       | | +-{ControllerName}Controller.php  # Backend controller
| |       | +-{ControllerName}Controller.php    # Frontend controller
| |       +-etc
| |       | +-adminhtml.xml  # Admin ACL and other settings
| |       | +-config.xml     # Configuration settings for your module
| |       | +-system.xml     # Administration settings and form options
| |       +-Helper
| |       | +-Data.php
| |       +-Model
| |       | +-Resource
| |       | | +-{EntityName}
| |       | | |  +-Collection.php  # Collection model for {entity}
| |       | | +-{EntityName}.php   # Resource model for {entity}
| |       | +-Observer.php         # Used for subscribing to Magento events
| |       | +-{EntityName}.php     # Data model for {entity}
| |       +-sql
| |       | +-{namespace}_{module}_setup
| |       |   +-mysql4-install-{X}.{X}.{X}.php
| |       |   +-mysql4-upgrade-{X}.{X}.{X}-{X}.{X}.{X}.php
| |       +-Test
| +-design
| | +-adminhtml
| | | +-default
| | |   +-default
| | |     +-layout
| | |     | +-{namespace}
| | |     |   +-{module}.xml
| | |     +-template
| | |       +-{namespace}
| | |         +-{module}
| | +-frontend
| |   +-base
| |     +-default
| |       +-layout
| |       | +-{namespace}
| |       |   +-{module}.xml
| |       +-template
| |         +-{namespace}
| |           +-{module}
| +-etc
|   +-modules
|     +-{Namespace}_{Module}.xml
+-skin
  +-adminhtml
  | +-default
  |   +-default
  |     +-css
  |     | +-{namespace}
  |     |   +-{module}
  |     +-images
  |     | +-{namespace}
  |     |   +-{module}
  |     +-js
  |       +-{namespace}
  |         +-{module}
  +-frontend
    +-base
      +-default
        +-css
        | +-{namespace}
        |   +-{module}
        +-images
        | +-{namespace}
        |   +-{module}
        +-js
          +-{namespace}
            +-{module}
```

<a name="setup"></a>
## Setup

<a name="step1"></a>
### 1. Tell Magento how to load your module

Magento needs to know that it should load your module and where to find it. For this, create an XML file under `app/etc/modules/{Namespace}_{Module}.xml`:

```xml
<?xml version="1.0"?>
<config>
    <modules>
        <{Namespace}_{Example}>
            <active>true</active>
            <codePool>local</codePool>
            <!-- Remove this section if your module does not depend on other Magento modules -->
            <depends>
                <Mage_Core/>
            </depends>
        </{Namespace}_{Example}>
    </modules>
</config>
```

The `<depends>` block above is for illustrative purposes only. If your module requires others to be loaded before it, list them under `<depends>` - otherwise you can remove it or replace it with an empty node (`<depends/>`).

<a name="step2"></a>
### 2. Create your module's configuration

Create your module's `config.xml` under `app/code/local/{Namespace}/{Module}/etc`. Again, not all sections are required and it will greatly depend on your module and what it needs - however, this example covers the most common use cases:

```xml
<?xml version="1.0"?>
<config>
    <modules>
        <{Namespace}_{Example}>
            <version>{X}.{X}.{X}</version>
        </{Namespace}_{Example}>
    </modules>
    <global>
        <blocks>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Block</class>
            </{namespace}_{module}>
        </blocks>
        <helpers>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Helper</class>
            </{namespace}_{module}>
        </helpers>
        <models>
            <{namespace}_{module}>
                <class>{Namespace}_{Example}_Model</class>
                <resourceModel>{namespace}_{module}_resource</resourceModel>
            </{namespace}_{module}>
            <{namespace}_{module}_resource>
                <class>{Namespace}_{Example}_Model_Resource</class>
                <!-- Remove this section if your module does not require any custom database tables -->
                <entities>
                    <{entity_name}}><table>{namespace}_{module}_{table_name}</table></{entity_name}>
                </entities>
            </{namespace}_{module}_resource>
        </models>
        <resources>
            <{namespace}_{module}_setup>
                <setup>
                    <module>{Namespace}_{Example}</module>
                </setup>
                <connection>
                    <use>core_setup</use>
                </connection>
            </{namespace}_{module}_setup>
            <{namespace}_{module}_write>
                <connection>
                    <use>core_write</use>
                </connection>
            </{namespace}_{module}_write>
            <{namespace}_{module}_read>
                <connection>
                    <use>core_read</use>
                </connection>
            </{namespace}_{module}_read>
        </resources>
        <!-- Remove this section if your module does not require any event observers -->
        <events>
            <{event_name}>
                <observers>
                    <{namespace}_{module}_{event_name}>
                        <type>model</type>
                        <class>{namespace}_{module}/observer</class>
                        <method>{methodName}</method>
                    </{namespace}_{module}_{event_name}>
                </observers>
            </{event_name}>
        </events>
    </global>
    <admin>
         <!-- Remove this section if your module does not have any admin controllers -->
         <routers>
            <adminhtml>
                <args>
                    <modules>
                        <{namespace}_{module} before="Mage_Adminhtml">{Namespace}_{Example}_Adminhtml</{namespace}_{module}>
                    </modules>
                </args>
            </adminhtml>
        </routers>
    </admin>
    <adminhtml>
        <!-- Remove this section if your module does not require admin layout updates -->
        <layout>
            <updates>
                <{namespace}_{module}>
                    <file>{namespace}/{module}.xml</file>
                </{namespace}_{module}>
            </updates>
        </layout>
    </adminhtml>
    <frontend>
        <!-- Remove this section if your module does not have any frontend controllers -->
        <routers>
            <{namespace}_{module}>
                <use>standard</use>
                <args>
                    <module>{Namespace}_{Example}</module>
                    <frontName>{namespace}</frontName>
                </args>
            </{namespace}_{module}>
        </routers>
        <!-- Remove this section if your module does not require frontend layout updates -->
        <layout>
            <updates>
                <{namespace}_{module}>
                    <file>{namespace}/{module}.xml</file>
                </{namespace}_{module}>
            </updates>
        </layout>
    </frontend>
    <!-- Remove this section if your module does not have system configuration -->
    <default>
        <{namespace}_{module}>
            <{group_name}>
                <enabled>0</enabled>
                <debug>0</debug>
            </{group_name}>
        </{namespace}_{module}>
    </default>
    <!-- Remove this section if your module does not require a cron task -->
    <crontab>
        <jobs>
            <{namespace}_{module}_{job_name}>
                <schedule><cron_expr>* * * * *</cron_expr></schedule>
                <run><model>{namespace}_{module}/observer::{methodName}</model></run>
            </{namespace}_{module}_{job_name}>
        </jobs>
    </crontab>
</config>
```

The comments above should explain which sections can be removed if your module does not require/need them.

> **Note:** Be sure to replace `{X}.{X}.{X}` with your module's version number (Example: `1.0.0`). This number is stored in the database table `core_resource` and is also used for running module setup scripts under `app/code/local/{Namespace}/{Module}/sql/{namespace}_{module}_setup`.

<a name="step3"></a>
### 3. Create your module's administration settings (optional)

Create the file `system.xml` under `app/code/local/{Namespace}/{Module}/etc`. Within this file you can define custom admin configuration tabs, admin settings, etc. Two example settings are included below (`enabled` and `debug`) which provide simple on/off settings in the Magento administration interface.

```xml
<?xml version="1.0"?>
<config>
    <tabs>
        <{namespace}_{module} translate="label" module="{namespace}_{module}">
            <label>{Namespace}</label>
            <sort_order>300</sort_order>
        </{namespace}_{module}>
    </tabs>
    <sections>
        <{namespace}_{module} translate="label" module="{namespace}_{module}">
            <label>{Section Label Text}</label>
            <tab>{namespace}_{module}</tab>
            <sort_order>1</sort_order>
            <show_in_default>1</show_in_default>
            <show_in_website>1</show_in_website>
            <show_in_store>1</show_in_store>
            <groups>
                <{group_name} translate="label">
                    <label>{Group Label Text}</label>
                    <sort_order>1</sort_order>
                    <show_in_default>1</show_in_default>
                    <show_in_website>1</show_in_website>
                    <show_in_store>1</show_in_store>
                    <fields>
                        <enabled translate="label">
                            <label>Enable Module</label>
                            <frontend_type>select</frontend_type>
                            <source_model>adminhtml/system_config_source_yesno</source_model>
                            <sort_order>1</sort_order>
                            <show_in_default>1</show_in_default>
                            <show_in_website>0</show_in_website>
                            <show_in_store>0</show_in_store>
                        </enabled>
                        <debug translate="label">
                            <depends><enabled>1</enabled></depends>
                            <label>Debug</label>
                            <frontend_type>select</frontend_type>
                            <source_model>adminhtml/system_config_source_enabledisable</source_model>
                            <sort_order>2</sort_order>
                            <show_in_default>1</show_in_default>
                            <show_in_website>0</show_in_website>
                            <show_in_store>0</show_in_store>
                        </debug>
                    </fields>
                </{group_name}>
            </groups>
        </{namespace}_{module}>
    </sections>
</config>
```

> **Note:** Each setting relates to the `<default>` key in `config.xml` - which specifies that setting's default value.

In order for the settings to show up/work - you must also create ACL rules for your new admin config section. For that, we need to create `adminhtml.xml` under `app/code/local/{Namespace}/{Module}/etc`.

```xml
<?xml version="1.0"?>
<config>
    <acl>
        <resources>
            <admin>
                <children>
                    <system>
                        <children>
                            <config>
                                <children>
                                    <{namespace}_{module] translate="title" module="{namespace}_{module]">
                                        <title>{Namespace} {Module}</title>
                                        <sort_order>1</sort_order>
                                    </{namespace}_{module]>
                                </children>
                            </config>
                        </children>
                    </system>
                </children>
            </admin>
        </resources>
    </acl>
</config>
```

> **Note:** For older Magento versions, it is necessary to also specify the above `<acl>` area under the `<adminhtml>` section of `config.xml`.

<a name="classes"></a>
## Write your module classes

<a name="blocks"></a>
### Blocks

Blocks control the HTML output of a specific section/area of various pages within Magento. You can create your own blocks but the most common use is to extend another Magento block.

```php
<?php

class {Namespace}_{Module}_Block_{BlockName} extends Mage_Core_Block_Template // For Adminhtml, extend: Mage_Adminhtml_Block_Abstract
{

}
```

<a name="controllers"></a>
### Controllers

Controllers are broken into 2 types: [frontend](#frontend) and [backend](#backend) (admin). The difference requires extending different base Magento classes.

<a name="frontend"></a>
#### Frontend

```php
<?php

class {Namespace}_{Module}_{ControllerName}Controller extends Mage_Core_Controller_Front_Action
{
    /**
     * Maps to: /{namespace}/{controllerName}/{actionName}/
     */
    public function {actionName}Action()
    {
        // Example of retrieving a query parameter
        $queryParameter = $this->getRequest()->getParam('query_parameter', 'Default Value (if not present)');

        // Example of getting a URL from the router
        $url = Mage::app()->getStore()->getUrl('{module}/{controller}');

        // Example of performing a redirect
        $this->_redirectUrl($url);
    }
}
```

<a name="backend"></a>
#### Backend (Admin)

```php
<?php

class {Namespace}_{Module}_Adminhtml_{ControllerName}Controller extends Mage_Adminhtml_Controller_Action
{
    protected function _initAction()
    {
        $this->loadLayout()
            ->_setActiveMenu('{menu_name}')
            ->_addBreadcrumb(
                '{Breadcrumb Text}',
                '{Breadcrumb Text}',
                // ...
            );
        return $this;
    }

    public function {actionName}Action()
    {
        $this->_title('{Title Text}');
        $this->_initAction()->renderLayout();

        // Example of adding a success notice message
        Mage::getSingleton('adminhtml/session')->addSuccess('{Success Message Text}');

        // Example of adding an error notice message
        Mage::getSingleton('adminhtml/session')->addError('{Error Message Text}');
    }
}
```

<a name="helpers"></a>
### Helpers

You must create one Helper class, however - it can remain empty. These classes are used for general functions/methods that are required between different class types (Example: retrieving configuration values).

```php
<?php

class {Namespace}_{Example}_Helper_Data extends Mage_Core_Helper_Abstract
{
}
```

> **Note:** This class can then be retrieved with: `Mage::helper('{namespace}_{module}')`

<a name="models"></a>
### Models

Models can be broken into 2 types: [data models](#data) and [resource models](#resource). Resource models control the interaction with the database (MySQL) whereas data models can range in responsibilities but usually manipulate data between controllers and resource models.

<a name="data"></a>
#### Data Model

```php
<?php

class {Namespace}_{Module}_Model_{EntityName} extends Mage_Core_Model_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}');
    }
}
```

> **Note:** This class can then be retrieved with: `Mage::getModel('{namespace}_{module}/{entity_name}')`

<a name="resource"></a>
#### Resource Model

```php
<?php

class {Namespace}_{Module}_Model_Resource_{EntityName} extends Mage_Core_Model_Mysql4_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}', '{primary_key}');
    }
}
```

> **Note:** This class can then be retrieved with: `Mage::getResourceModel('{namespace}_{module}/{entity_name}')` However, it is common practice to retrieve it from the data model instance: `Mage::getModel('{namespace}_{module}/{entity_name}')->getResource()`

You can also (optionally) define the Collection class used. The Collection is used to handle many instances of your resource models (saving many rows, retrieving many rows, iterating, etc.).

```php
<?php

class {Namespace}_{Module}_Model_Resource_{EntityName}_Collection extends Mage_Core_Model_Mysql4_Collection_Abstract
{
    protected function _construct()
    {
        $this->_init('{namespace}_{module}/{entity_name}');
    }
}
```

> **Note:** This class can then be retrieved from the data modal instance with: `Mage::getModel('{namespace}_{module}/{entity_name}')->getCollection()`

<a name="observers"></a>
#### Observers

The easiest and most flexible way of extending Magento features is by listening and responding to events with an observer class. Which events your module listens for is defined in your module's `config.xml`.

```php
<?php

class {Namespace}_{Module}_Model_Observer
{
    public function {methodName}(Varien_Event_Observer $observer)
    {
        return $this;
    }
}
```

<a name="extending"></a>
## Extending Magento classes

Extending a Magento (or other module) class is relatively easy. For blocks, helpers, models, and resource models just use the following syntax in your module's `config.xml` (under `<blocks>`, `<models>`, etc.) to rewrite a Magento class to yours:

```xml
            <{module_to_override}>
                <rewrite>
                    <{class_to_override}>{Namespace}_{Module}_Block_{ClassToOverride}</{class_to_override}>
                </rewrite>
            </{module_to_override}>
```

Here is an example of rewriting `Mage_Core_Model_Email_Template` with `Acme_Custom_Model_Email_Template`:

```xml
<?xml version="1.0"?>
<config>
    <global>
        <models>
            <core>
                <rewrite>
                    <email_template>Acme_Custom_Model_Email_Message</email_template>
                </rewrite>
            </core>
        </models>
    </global>
</config>
```

> **Caution:** It is important to remember that core Magento modules (those namespaced with `Mage_`) do not require the use of `mage_`. So the example above uses just `core` rather than `mage_core`.

<a name="tips"></a>
## Tips

#### `var_dump()` and Magento

Trying to `var_dump()` a Magento class instance will quickly lead to headaches because of circular references. Most Magento classes extend `Varien_Object` and thus expose a `debug()` method which is much better for dumping:

```php
<?php

var_dump($object->debug());
```

#### Logging

The easiest way to write to the system logger (or your own custom log file) is to use the `log()` method exposed by the `Mage` class:

```php
<?php

Mage::log('{Log Message Text}', (int) '{(optional) Log Level}', '{(optional) Log Filename}', (bool) '{(optional) Force Writing}');
```