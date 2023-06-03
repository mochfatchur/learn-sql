- Problem : https://leetcode.com/problems/actors-and-directors-who-cooperated-at-least-three-times/

    ```sql
    SELECT actor_id, director_id
    FROM ActorDirector
    GROUP BY actor_id, director_id
    HAVING COUNT(director_id) >= 3;
    ```
- exp: count the every unique director_id by grouping the director_id by grouping the actor_id

- https://leetcode.com/problems/triangle-judgement/
    ```sql
    SELECT x, y, z, IF ( x+y>z AND y+z>x AND x+z>y, 'Yes', 'No') AS triangle
    FROM triangle;
    ```
- exp : just use if or case when


- Problem : https://leetcode.com/problems/product-sales-analysis-i/

    ```sql
    SELECT p.product_name, s.year, s.price
    FROM Sales s
    INNER JOIN Product p ON s.product_id = p.product_id;
    ```
- exp: the keyword why we use INNER JOIN is "<br>for each</br> sale_id in the Sales table"