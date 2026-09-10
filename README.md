Fastburgers Database Summary

This database manages operations for a fast-food restaurant chain. It tracks customer orders, menu items, order details, restaurant outlets, and staff members across different locations.

Database Structure

The schema includes five core tables:

customers: Stores customer profile details.

menu_item: Contains the list of food items, pricing, and descriptions.

orders: Tracks individual customer transactions and locations.

order_item: Links ordered items and their quantities to specific orders.

staffs: Holds employee details and their assigned outlet.

Queries Used:

-- 1. Get staff names, roles, and their working outlet location
SELECT 
    s.name AS staff_name, 
    s.role, 
    o.location
FROM fastburgers.staffs s
JOIN fastburgers.outlet o 
    ON s.outlet_id = o.outlet_id;

-- 2. Find morning menu items ending before 12:00 PM
SELECT 
    menu_name, 
    end_time
FROM menu
WHERE end_time < '12:00';

-- 3. Retrieve high-quantity order line items (2 or more items)
SELECT 
    order_id, 
    item_id, 
    quantity
FROM order_item
WHERE quantity >= 2;
