<h1 align="center">A Developer Guide</h1>
<br />
Some tips and tricks and help navigating various certifications.





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