Solution
===================================================================================================

SELECT pages.page_id FROM pages
LEFT JOIN page_likes ON (pages.page_id=page_likes.page_id)
WHERE liked_date IS NULL
ORDER BY page_id;


===================================================================================================
Problem
===================================================================================================

Assume you're given two tables containing data about Facebook Pages and their respective likes (as in "Like a Facebook Page").

Write a query to return the IDs of the Facebook pages that have zero likes. The output should be sorted in ascending order based on the page IDs.

Table: pages

+-------------+-----------+
| Column Name | Type      |
+-------------+-----------+
| page_id     | int       |
| page_name   | varchar   |
+-------------+-----------+

Example Input of pages table:

+-------------+--------------------------+
| page_id     | page_name                |
+-------------+--------------------------+
| 20001       | SQL Solutions            |
| 20045       | Brain Exercises          |
| 20701       | Tips for Data Analysts   |
+-------------+--------------------------+

Table: page_likes

+-------------+-----------+
| Column Name | Type      |
+-------------+-----------+
| user_id     | int       |
| page_id     | int       |
| liked_date  | datetime  |
+-------------+-----------+

Example Input of pages table:

+----------+---------------------------------+
| user_id  | page_id  |      liked_date      |
+----------+----------+----------------------+
| 111      | 20001    |  04/08/2022 00:00:00 |
| 121      | 20045    |  03/12/2022 00:00:00 |
| 156      | 20001    |  07/25/2022 00:00:00 |
+----------+----------|----------------------+


Example Output:

+---- ----+
| page_id |
+---------+
| 20701   |
