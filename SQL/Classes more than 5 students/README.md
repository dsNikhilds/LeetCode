# Write your MySQL query statement below

SELECT class

FROM (

    SELECT class,COUNT(DISTINCT student) AS count
    
    FROM Courses
    
    GROUP BY class) AS sub
    
WHERE count >= 5
;
