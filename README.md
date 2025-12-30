📄 README.md
🏰 Project Realm
    The Pizza Sales Lab Project is a relational database designed to manage the daily operations of a pizzeria. It acts as the "Single Source of Truth" for menu management, inventory tracking, and sales analytics.

📜 Core Features
  Menu Management: Detailed tracking of pizza names, categories, sizes, and ingredients.

  Sales Ledger: Recording of customer orders, including dates, precise timestamps, and individual line items.
  
  Financial Tracking: Management of unit pricing and total order calculations.
  
  Inventory Oversight: Monitoring stock levels for various pizza types and sizes.

🛠️ Technical Stack
    Database Engine: MariaDB (Localhost via phpMyAdmin).
    
    Language: SQL (DDL, DML).
    
    Character Set: utf8mb4_general_ci.
    
🗺️ Entity Relationship Diagram (ERD)
    The database uses a Star-like Schema where the Pizzas table acts as the central dimension for product data, and OrderItems/CustomerOrders act as the primary fact tables.
    
    📚 Data Dictionary
    🍕 1. Table: Pizzas
    The master catalog of all pizza variants.

    pizza_id: (Primary Key) Unique identifier for each specific pizza variant.
    
    pizza_name: The common name of the pizza (e.g., "The Hawaiian Pizza").
    
    pizza_size: The size classification: S, M, L, or XL.
    
    pizza_category: Grouping by flavor profile: Classic, Veggie, Supreme, or Chicken.
    
    pizza_ingredients: A text list of the standard toppings.

📜 2. Table: PizzaOrders
    High-level transactional records.
    
    order_id: (Primary Key) Unique ID for every customer transaction.
    
    pizza_id: Links to the primary pizza in the order.
    
    order_date: The date the order was placed.
    
    order_time: The exact time of the transaction.
    
    total_price: The final monetary value of the order.
    
🛍️ 3. Table: OrderItems
    Granular line items for every order.
    
    order_item_id: (Primary Key) Unique ID for each line item.
    
    order_id: (Foreign Key) References PizzaOrders.
    
    pizza_id: (Foreign Key) References Pizzas.
    
    quantity: The number of units of that specific pizza.
    
    unit_price: The price per single unit.
    
    total_price: Calculated as quantity * unit_price.
    
📦 4. Table: PizzaInventory
    Tracks the kingdom's stock.
    
    inventory_id: (Primary Key) Unique ID for the stock record.
    
    pizza_id: (Foreign Key) References the specific pizza type.
    
    quantity: Current count of items in stock.

🛡️ Data Integrity & Constraints
    To ensure the scrolls of data remain accurate, the following rules are enforced:
    
    Referential Integrity: Constraints ensure that an order cannot exist for a pizza_id that is not in the master Pizzas table.
    
    Date Consistency: Transactions are tracked with standard DATE and TIME types for chronological accuracy.
    
    Financial Precision: Prices use DECIMAL(10,2) to prevent rounding errors during calculations.

🧙‍♂️ Sample Insights from the Lore
    Oldest Recorded Order: Order ID 1, placed on 2015-01-01 at 11:38:36.
    
    Premium Offering: The "Five Cheese Pizza" (Large) is a popular choice in the Veggie category.
    
    Value Offering: The "Pepperoni Pizza" (Small) represents one of the most affordable entry points on the menu.
