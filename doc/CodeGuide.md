Hello, Developer - Code
=======================

Rules are meant to be broken. Styles are meant to be consistent.


Rationale
---------

A source of frustration for most developers, at least for me, has always been 
the realization and application of good coding practices. They are commonly 
under-appreciated. It saves time, can save money, and also allows to focus on 
the more subjective topics of coding. The ones worth spending time on.

You can support a project with the wrong developer using the right standards, but 
you can't support the right developers using the wrong standards. Meaning as 
long as you have the right guidelines, the rest will take care of itself.


Table of Contents
-----------------

 1. [Introduction](#introduction)
 2. [Code Style and Principles](#code-style-and-principles)
 2. [Documentation Styles and Standards](#documentation-styles-and-standards)
 3. [Benchmarking and Performance Standards](#benchmarking-and-performance-standards)
 4. [Testing and Quality Assurance](#testing-and-quality-assurance)
 5. [Best Practices](#best-practices)
 6. [Further Reading](#further-reading)


Introduction
------------

1. Brings consistency to my code
2. Saves time from stupid conversations in my head about style
3. Automates patterns for testing in pre and post deployments

All guides are public for sake of expectation and objection. If there is ever an
action in question, the reason why is always available for discussion.

That said, opinions change, rules are meant to be broken.


### General Considerations

My styles are specific to publishing years of random work and learning more.

PLEASE GO USE SOMEONE ELSES.


### Preference

My interpretation or modification has started with Magento, PSR-1, PSR-2, and 
Google. If it is not in those four guides, then I did not pay attention to it 
and it probably has been repeated, incorrect, or done before.


## Code Styles and Principles

### [1.1](#code-styles-and-principles--principles) Principles

Write your code as if someone else is going to read it to understand it.

Codification of the styles and processes I have inherited over the years.

Single source of truth for my reason of action.

Exists as a LIVING document. It provides guidelines for writing ioDS code, sample
code, documentation, libraries, and apps.

This is not my Bible. Rules are mean't to be broken. This is also to be taken a la carte

Not perscriptive. Just my application and interpretation of practices.

Blind Communication
Small, Composible Modules
Convention Over Configuration
Behavior Driven Development
KISS
Don't Re-Invent the Wheel


### [1.2](#code-styles-and-principles--styles) Styles

#### [1.2.1](#styles--document-formatting) Document Formatting

PHP code MUST always begin with the long form opening tag and include an end tag.

The exception to this is when a file contains only PHP.

```php
<?php
    // right way
?>

<?= // wrong way ?>
```


## Documentation Styles and Standards

Document your code as if someone else is going to extend it, and profit from it.


## Benchmarking and Performance Standards

@TODO


## Testing and Quality Assurance

@TODO


## Best Practices

 * Constructors take options objects.
 * Inheritance should use Trait-like patterns. Abstract methods meant to be
   implemented by modules extending it.
 * Think before you code

### [1.2](#best-practices--procesess) Processes

Git and stuff.


## Further Reading

@TODO