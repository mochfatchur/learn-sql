- Problem: https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/

    ```sql
    SELECT customer_number
    FROM Orders
    GROUP BY customer_number
    HAVING COUNT(*) = (
        SELECT COUNT(*)
        FROM Orders
        GROUP BY customer_number
        ORDER BY COUNT(*) DESC
        LIMIT 1
    );
    ```
- explaination: 
find the largest number of orders from the customer_number, and the you will get (COUNT(customer_number with largest number of order)) => count of number order for every customer_number.
    ```sql
        ..............(
        SELECT COUNT(*)
        FROM Orders
        GROUP BY customer_number
        ORDER BY COUNT(*) DESC
        LIMIT 1
        );
    ```
- then get the every customer_number that have count of number order that equal to the largest number of orders.
    ```sql
    SELECT customer_number
    FROM Orders
    GROUP BY customer_number
    HAVING COUNT(*) = (
    "COUNT(customer_number with largest number of order)"
    );
    ```
