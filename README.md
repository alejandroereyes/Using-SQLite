Normal Mode
-----------
- There are 50 users.

  sqlite> SELECT count(*) FROM users;
  count(*)
  50

- Five most expensive items:
   1) Small Cotton Gloves
   2) Small Wooden Computer
   3) Awesome Ganite Pants
   4) Sleek Wooden Hat
   5) Ergonomic Steel Car

   sqlite> SELECT * FROM items ORDER BY price DESC LIMIT(5);
  id|title|category|description|price
  25|Small Cotton Gloves|Automotive, Shoes & Beauty|Multi-layered modular service-desk|9984
  83|Small Wooden Computer|Health|Re-engineered fault-tolerant adapter|9859
  100|Awesome Granite Pants|Toys & Books|Upgradable 24/7 access|9790
  40|Sleek Wooden Hat|Music & Baby|Quality-focused heuristic info-mediaries|9390
  60|Ergonomic Steel Car|Books & Outdoors|Enterprise-wide secondary firmware|9341

- The cheapest book is from the Books only category is "Fantastic Steel Chair"

  sqlite> SELECT * FROM items WHERE category = 'Books' ORDER BY price DESC LIMIT(1);
  id|title|category|description|price
  4|Fantastic Steel Chair|Books|Advanced attitude-oriented encryption|9246

 The cheapest book when opening the search to any category with a Books is "Awesome Granite Pants"

  sqlite> SELECT * FROM items WHERE category LIKE "%Books%" ORDER BY price DESC LIMIT(1);
  id|title|category|description|price
  100|Awesome Granite Pants|Toys & Books|Upgradable 24/7 access|9790

-  Corrin Little lives at 6439 Zetta Hills, Willmouth, WY. 2nd address at 54369 Wolff Forges, Lake Bryon CA 31587.

  sqlite> SELECT * FROM addresses WHERE street = '6439 Zetta Hills';
  id|user_id|street|city|state|zip
  43|40|6439 Zetta Hills|Willmouth|WY|15029

  sqlite> SELECT * FROM users WHERE id = 40;
  id|first_name|last_name|email
  40|Corrine|Little|rubie_kovacek@grimes.net

  ssqlite> SELECT * FROM addresses WHERE user_id = 40;
  id|user_id|street|city|state|zip
  43|40|6439 Zetta Hills|Willmouth|WY|15029
  44|40|54369 Wolff Forges|Lake Bryon|CA|31587

- Virinie Mitchell's address has been updated shown on lines 61 & 62.
  sqlite> SELECT * FROM users WHERE first_name = 'Virginie';
  id|first_name|last_name|email
  39|Virginie|Mitchell|daisy.crist@altenwerthmonahan.biz

  sqlite> UPDATE addresses SET city = 'New York' WHERE user_id = 39;
  sqlite> UPDATE addresses SET zip = 10108  WHERE user_id = 39;

  sqlite> SELECT * FROM addresses WHERE user_id = 39;
  id|user_id|street|city|state|zip
  41|39|12263 Jake Crossing|New York|NY|10108
  42|39|83221 Mafalda Canyon|New York|WY|10108

- It would cost $7383 to buy one of each tool.

  sqlite> SELECT SUM(price) FROM items WHERE category = 'Tools';
  SUM(price)
  7383

- 2125 items were sold.

  sqlite> SELECT SUM(quantity) FROM orders;
  SUM(quantity)
  2125

- Total amount spent on books $420,566

  sqlite> SELECT SUM(price*quantity) FROM orders JOIN items ON orders.item_id = items.id WHERE category = 'Books';
  SUM(price*quantity)
  -------------------
  420566

- sqlite> INSERT INTO users (id, first_name, last_name, email) VALUES (51, 'Alex', 'Reyes', 'ar@tiy.com');

  sqlite> INSERT INTO orders (id, user_id, item_id, quantity, created_at) VALUES (378, 51, 91, 3, CURRENT_TIMESTAMP);

















