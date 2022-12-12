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