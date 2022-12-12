# Section 5: Catalog (22%)

[Previous Section](./4.md) | [Table of Contents](./)

-----


## [Section 5: Catalog (22%)](./5.md) - 700

### **5.1** Demonstrate how to use products

#### **Demonstrate the ability to create and use product videos. What determines whether a product is visible on the storefront? What determines whether a product can be sold on the storefront (saleable)?**

### **5.2** Demonstrate ability to use different product types

#### **What are product types in Magento Commerce?**

### **5.3** Demonstrate ability to use categories

#### **How can products and categories be added? What is the visual merchandiser? How can the visual merchandiser be used? Demonstrate the ability to manage categories. How can multiple websites with independent category trees be created?**

### **5.4** Demonstrate ability to use product attributes

#### **What are attribute sets? What are the consequences of a few large attribute sets vs. many small attribute sets? What is the effect of using many configurable attributes with a product? What is the effect of store scope vs. global scope attributes? What are possible strategies to use fewer product attributes?**

### **5.5** Demonstrate ability to scale catalogs

#### **How to deal with large catalogs**

#### **High SKU catalogs**

#### **High volume sales**

### **5.6** Demonstrate ability to configure inventory management

#### **Inventory management**





## [Section 6: Customizing the Catalog (23%)](./6.md)  - 704

### **6.1**  Demonstrate an ability to understand and customize Magento products

#### **Selecting the right product type for a given requirement (configurable with custom options, bundle with grouped). Deciding to use non-standard products: for example, for licenses, subscriptions, courseware, or glasses. Product relations (related, upsells).**

#### **Select a product type for a subscription/subscription bundled with a physical product**

#### **Select a product type for courseware**

#### **Select a product type for glasses with a prescription**

#### **Compare custom options with configurable products**

#### **Configurable product with custom options for the associated simple products**

#### **Bundled product with custom options for its associated simple products**

#### **What is the "related products" database structure? Understand the performance impact of having many related products**

#### **Compare related with upsells**

#### **Programmatically access related products, custom options, configurable parameters**

#### **Dynamic related products**

### **6.2**  Demonstrate an ability to perform complex operations with the Magento pricing framework


#### **Understand the pricing calculation and rendering framework. Which classes are involved in rendering/calculation? What is the role of indexing? How do different price modifiers work together?**

#### **How is a price calculated on the product detail page, the product listing page? Price calculation classes. Relation to the price indexer**

#### **The `Magento\Framework\Price\*` component and its extension in the Catalog module**

#### **How to render a product price: which class to use, which data needs to be provided**

#### **Indexed price vs. prices calculated on the fly**

#### **Price configuration: tier prices, special price, custom option, configurable adjustment, catalog rules, cart rules**

#### **How to change the price rendering process for a given product type/product instance**

#### **How to add a custom price adjustment to modify the calculation process. What happens if the price index is not aligned with this change?**

### **6.3**  Customize catalog price rules


#### **Programmatically create a catalog price rule, the impact of catalog price rules on performance, extending catalog price rule conditions with custom entities**

### **6.4**  Determine how to use Magento categories


#### **Advanced category features: hierarchy, custom attributes, impact on performance**

#### **What happens if a project has many categories?**

#### **Dynamic rules for the order of products in category**

#### **The category `is_anchor` attribute and its effect on performance**

### **6.5**  Demonstrate an understanding of catalog indexers


#### **The indexing framework, the price indexer, the inventory indexer, the EAV indexer. How does Magento use indexed data?**

#### **Estimate indexing customization efforts when making architectural decisions. Estimate indexing process complexity and time for different given conditions. The impact of indexing for frequent catalog updates.**

#### **What steps does Magento perform when indexing? What is the role of the indexer_state table**

#### **How to register a new indexer**

#### **How does the price indexer work? Which events trigger it? How do different product types declare their indexers? How important is an order of indexers in price indexing?**

#### **Inventory indexer overview, inventory indexing for different product types**

#### **What is the scope of a price in the price index? How difficult is it to extend the scope of an index?**

#### **Impact of many stores/websites on price indexing**

#### **Custom price modifiers: Pros and cons of customizing the index versus adjusting the native features like price rules or custom options**

### **6.6**  Demonstrate understanding of catalog staging and its impact on the system


#### **Flow modifications introduced by staging (triggers, row_id, data versions). Staging-related modifications of the indexing process**

#### **Issues related to different `row_id` and `entity_id`**

#### **Catalog triggers**

### **6.7**  Demonstrate an understanding of the product search framework


#### **How to customize Elastic search**

### **6.8**  Demonstrate understanding of importing products and categories in Magento

#### **Frequent imports, massive imports, import with many attributes**

#### **Issues related to a frequent import, for example every minute**

#### **Compare importing products using the native import, save by model, or custom SQL**

#### **Specifics of importing a catalog with many attributes and attribute sets**

#### **Importing categories and product relations**





