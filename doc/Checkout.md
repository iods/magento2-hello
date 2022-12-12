# Section 7: Customizing the Checkout Process (17%)

[Previous Section](./6.md) | [Next Section](./8.md)

-----

## [Section 7: Customizing the Checkout Process (17%)](./7.md)

### **7.1**  Understand the Magento quote architecture and customizing quote-related functionality

#### **Quote-related objects, total models and price calculation process, the add to cart process, custom add to cart operations, customizations of the price calculation, taxes and discount, various display settings**

#### **The quote merge functionality**

#### **Programmatically add a "free gift" when a certain condition is met**

#### **Programmatically set a price for a product**

#### **Taxes with discounts calculation**

#### **The impact of many shopping cart price rules on performance**

#### **Programmatically create shopping cart price rules**

#### **Importing coupon codes**

#### **Extend the shopping cart price rules with custom entities**

#### **Programmatically separate line items in the shopping cart so there are two line items instead of one with qty=2**

#### **Adding a new total model and evaluating its impact on taxes and discounts**

#### **Shipping discounts behavior and customizations**

#### **WebAPI for quote operations. Create a quote, add an item, create a coupon, add a discount**

### **7.2**  Demonstrate an ability to customize and extend the checkout process

#### **Checkout steps, the REST API, customizations of the checkout API, the order placement process. The impact of many concurrent order placements**

#### **Adding a step to the checkout after the payment step, or between the payment and shipping steps**

#### **Implementing a ""one-click"" checkout, evaluate possible pitfalls such as discounts being applied or canceled when the order is placed**

#### **The checkout REST API: Modifying the native flow (separate calls to save payment and to place the order)**

#### **Extending the checkout REST API. Adding new parameters to different API endpoints. Using extension attributes**

#### **Issues related to simultaneous order placement, inventory locking**

#### **Determining the exact moment when the stock is decremented during an order placement**

#### **Customizing the order placement such that it uses message queues**

#### **Horizontal sharding of orders tables to improve order placement capacity. What challenges need to be resolved?**

### **7.3**  Create and debug shipping and payment methods in Magento

#### **Different types of payment methods: gateway, offline, hosted. The gateway payment methods framework. The payment method availability logic. The shipping rates calculation process, debugging shipping rates and table rates customizations**

#### **The gateway framework vs. AbstractMethod**

#### **The structure of offline payment methods. What makes them "offline"?**

#### **Partial invoices/refunds for payment methods**

#### **Add a hosted-type payment method (redirects, custom order review page)**

#### **Add a new shipping method. Customize the logic for getting a list of available shipping methods**

#### **The shipping rate calculation flow. Debug shipping rates, identify plugins that that influence the shipping rate calculation process**

#### **Customizing table rates. Add a new "column" to the "table", change the logic of selecting the rate.**

#### **Gateway shipping methods. Remote call flow. How to avoid the remote call if it is unnecessary**


