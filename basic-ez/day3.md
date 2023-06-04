- Problem : https://leetcode.com/problems/students-and-examinations/

    ```sql
    SELECT 
    st.student_id, st.student_name, sb.subject_name, 
    COUNT(ex.subject_name) AS attended_exams
    FROM Students st
    CROSS JOIN Subjects sb
    LEFT JOIN 
    Examinations ex ON st.student_id = ex.student_id 
    AND sb.subject_name = ex.subject_name
    GROUP BY st.student_id, st.student_name, sb.subject_name
    ORDER BY st.student_id, sb.subject_name;
    ```
- exp : This query uses a combination of CROSS JOIN and LEFT JOIN to get all possible combinations of students and subjects. The LEFT JOIN ensures that even if a student didn't attend a particular exam, they will still be included in the result with a count of 0 for that exam. The COUNT function is used to count the number of attended exams for each combination. The result is then grouped by student ID, student name, and subject name, and ordered by student ID and subject name.

-  CROSS JOIN to cartesian product the __Students__ and __Subjects__ => so that each column in the __Students__ table corresponds to a column in the __Subjects__ table
- LEFT JOIN to LEFT JOIN ensures that even if a student didn't attend a particular exam, they will still be included in the result with a count of 0 for that exam

- Why we group 
    ```sql
    st.student_id, st.student_name
    ```
    we group by only that because we want for there is that is not be grouped is being counted, when we use __COUNT__