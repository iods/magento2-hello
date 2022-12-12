![Evino](https://blog.evino.com.br/wp-content/uploads/2018/09/logo-red.svg)
========  
Assessment test to evaluate skills of Magento Backend Developer candidates.

# Introdution
This assessment test aims to assessing your knowledge as a Magento Backend developer. The assessment test will assess your skills on:
- Your level of knowledge of the PHP OOP language (PHP version 7+)
- Magento component architecture (Magento Open Source/Commerce 2.3+);
- Knowledge of the main design patterns used by the platform
- Use of dependency injection
- Magento Plugins (Interceptors)
- Code standards and good programming practices
- SOLID Principles and PHP Standards Recommendations (PSR)
- Composer

# What will be evaluated?

- Structure and organization of code and files
- Adopted solutions
- Technologies used
- Quality
- PSR Patterns, Design Patterns
- Anyway, everything will be observed and taken into consideration

# How to publish your test?

- Create a private repository on GitHub
- Follow all the instructions for running the assessment test
- When finished, invite the GitHub user **evinoit** to access your repository and evaluate your assessment test
  (https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/inviting-collaborators-to-a-personal-repository)

# Instructions

The main focus of our assessment test is to evalute your skills and knowledge as a Magento Backend developer.

You have complete freedom to increase some knowledge that you find interesting to apply in the evaluation.

> There is no problem if you are unable to run all the features of the assessment, do as much as you can.

## Basic features
1. Module to create wine producer entities and associate them with products;
2. Use interfaces to create service contracts;
3. The module must have resources to create, edit, list and delete producers from Magento admin area;
4. The module access must be available in the Magento Admin area through the 'Content > Producers' menu;
5. It should be possible to restrict access to Magento Admin users to create, edit, delete and list producers;
6. The producer registration form must have:

| Field name       | Type        | Required | Additional checks                |
|------------------|-------------|----------|----------------------------------|
| Enable           | bool/UI toogle | Yes      |                                  |
| Producer Name    | text        | Yes      | alphanumeric, max 150 characters |
| Description      | textarea    | No       | max 600 characters               |
| Producer Image   | file/UI     | Yes      | PNG or JPG                       |
| Producer Website | text        | No       | Valid URL                        |

7.  Set up a dropdown product attribute to select the producer by name when creating a new product ad Magento admin area;
8. The product attribute must be created through the module's setup, and it must be possible to remove it when uninstalling the producer module
9. The dropdown product attribute must list only product entities that have the Enable = true
10. The product attribute must be available to layered navigation filtering
11. Translation for all labels and texts with i18n

## Advanced features
These additional requirements are a differential and will have greater weight in relation to another candidates

1. Import producers from CSV file using MAGENTO CLI command
2. Make the producer product attribute available in the GraphQl search at products query and aggregations;
3. All code must pass in Magento Static tests (Magento Coding standards);
4. Create unit tests to cover at last 50% of classes;
5. Create integration tests to cover:
    - Test producer create, list, edit and delete;
    - Test product creation with producer attribute;
6. MFTF to tests all Magento admin area implementations for Producer Module


# Magento testing scenarios
*For use after an upgrade to verify the correct working of Magento*

![SHIP IT](http://media.giphy.com/media/143vPc6b08locw/giphy.gif)

# Frontend

## General
- Activate all logs on the server (PHP, MySQL, Magento, mail, etc)
- Check meta tags in HTML
- Check favicon
- Check merging of CSS
- Check merging of JS
- Check Google Analytics
- Check for Javascript errors in Console
- Check header - all blocks present?
- Check footer - all blocks present?
- Check homepage
- Test newsletter subscription block
    - For new subscriber
    - For existing subscriber

## Catalog
- Click through all category pages and check for;
    - Layered navigation showing and working correctly
    - Sorting working correctly
    - Pager working correctly
    - Check breadcrumbs
- Open at least 30 product pages and check for;
    - Correct price
    - Add to cart button
    - Configurable options, if applicable
    - Images
- Check working of search
- Check working of Advanced Search

## Checkout

### Cart
- Add item to cart
- Add multiple items to cart
- Test Remove item button
- Test Update shopping cart button
- Test Clear shopping cart button
- Check correct price
- Check correct totals (discount/tax/etc)
- Test Proceed to checkout button
- Check pop-out shopping cart in top right, if applicable

### Onepage
- Check if login works
- Place a lot of orders;
    - Multiple products
    - With discounts
    - Let the transaction fail to see how Magento handles canceled orders
    - Try all combinations of payment methods & shipping methods
    - Try guest checkouts as well as logged-in checkouts
- Check if all fields that should be collapsed are collapsed

### OneStepCheckout
- All shipping methods available?
- All payment methods available?
- All enabled countries correct?
- Are the AJAX filled fields loading correctly?
- Does the login link work?
- No license warning showing?

## My Account
- Login & logout
- Are the correct My Accounts options showing?
- Reorder an order
- Add/edit address
- Subscribe / unsubscribe for newsletter

# Extensions
- Walk through all extensions and find out what their purpose is. This takes up the most of the work, but most extensions will have test cases that coincide with above test cases. For example; by placing an order you'll probably also test whether the order is sent to the warehouse or financial management system.

#Backend
- Clear cache
- Reindex all indexers
- Place an order through the backend
- Create a customer through the backend
- Open all pages to see whether exceptions occur
- Check all configuration options for all extensions in the backend
- Check tax setting
- Check transactional emails
- Check attributes and attribute sets


# Misc
- Check if crontab is set, start cron.php manually and check cron_schedule for errors
- Shell scripts
- After all previous test assignments, check all log files (Magento logs, PHP logs, MySQL logs, email logs)