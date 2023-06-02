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

- Problem: https://leetcode.com/problems/game-play-analysis-i/description/

    ```sql
    SELECT player_id, MIN(event_date) AS       first_login
    FROM Activity
    GROUP BY player_id;
    ```


    -   explanation: 
    just group by player_id, you will automatically get the first event_date for every row in player_id but just for safety we declare MIN(event_date) implicitly to get the first event_date.

