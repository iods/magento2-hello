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
 

 Rules for all style guides
Whether you build on an existing style guide or write one from scratch, follow these guidelines.

Be clear about the scope
If a guideline applies only to samples, then say so. For example, you might specify when and how a sample can omit exception handling.

Recommend tools
Find and recommend tools that can help developers produce code that conforms to your style guide. For example, you might recommend lint tools such as pylint and JSHint. Formatting tools like gofmt can help, too.

Minimize ambiguity
Avoid TMTOWTDI ("Tim Towdy" / "There's more than one way to do it") coding practices. Recommend a single way to do things where possible. Our samples do not need to use every feature of every language. They do need to be stylistically consistent.

Specify what the code can depend on
Specify when to use libraries and frameworks, and when to write ‘pure’ samples. Specify dependency versions to prevent compatibility issues.

Recommend a testing framework
Specify a testing framework in your guide. Pick a framework that is widely used, and which is easy for Dev Platform members to quickly learn to use (a JUnit based framework, for example).

Provide exception handling guidelines
Sample code is different from other code in that it primarily exists to demonstrate the use of a specific API or feature. For this reason, the sample author may want to simplify the code to the bare essentials. You can help the sample author by including in your guide recommendations for when it is acceptable to leave out exception handling.

Customizing an existing style guide
Here are some examples of how you might customize an existing style guide:

Simplifying directory structure: Your code uses a framework that recommends a specific directory structure. However, small samples can be more readable if they have fewer files and directories. Your style guide should help developers figure out a consistent way to consolidate code.

Removing complexity: You're building on a style guide that places no restrictions on using anonymous functions as the value of callback parameters. For better readability, though, you think it is better to have named functions. Consider suggesting modifications to the style guide to restrict the use of features that lead to readability problems.

Referencing other Dev Platform style guides
Don't duplicated content in another Dev Platform style guide. Instead, layer your style guide on top of existing guides. For example:

a polymer.js or node.js guide builds on top of the JavaScript guide.

an Android games guide builds on top of the Android guide, which builds on top of the Java guide.

Creating a style guide from scratch
** Do this only if there is no existing guide that you can use.**

Style guides are language specific and sometimes framework specific, but here is a list of topics that are likely to show up in most style guides. Address these in your guide:

Code layout
indentation
tabs or spaces?
maximum line length
continued line indentation
blank lines
block style (for example, where to put the { and }, and using {} vs. do ... end in Ruby)
Whitespace in expressions and statements
inside (), {}, [], etc.
around comma, colon, and semicolon
around operators
Comments
when to use block comments
when to use inline comments
how to write doc comments
Naming conventions
allowed/disallowed characters in names

use cases for the following:

lowercase
UPPERCASE
lowercase_with_underscores
UPPERCASE_WITH_UNDERSCORES
CapitalizedWords
camelCase
leading and trailing _ (single underscore)
leading and trailing __ (double underscore)
naming conventions for the following:

classes
exceptions
global variables
functions
function and method arguments
method names and instance variables
constants
filenames
module/library names
Sample directory structure
inline code vs. separate file
order of includes/imports
include/import DOs and DON’Ts
Scoping
use of namespaces
nested classes and functions
static members
policy on use (or disuse) of globals
local variables
Code organization
when to use which kind of constructor
multiple inheritance DOs and DON’Ts
mixin DOs and DON’Ts
operator overloading
function overloading
default arguments
use of const, final, etc.
when to use single, double, or triple quotes for strings
Using Markdown
Write your style guide using Github flavored Markdown. You can preview the rendered HTML by creating a Gist on Github and giving it a .markdown or .md extension.