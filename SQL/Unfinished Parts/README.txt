Solution
===================================================================================================

SELECT part, assembly_step FROM parts_assembly
WHERE finish_date IS NULL;


===================================================================================================
Problem
===================================================================================================

Tesla is investigating production bottlenecks and they need your help to extract the relevant data. Write a query to determine which parts have begun the assembly process but are not yet finished.

Assumptions:

- parts_assembly table contains all parts currently in production, each at varying stages of the assembly process.
- An unfinished part is one that lacks a finish_date.

Table: parts_assembly

+---------------+----------+
| Column Name   | Type     |
+---------------+----------+
| part          | string   |
| finish_date   | datetime |
| assembly_step | int      |
+---------------+----------+


Example Input of parts_assembly table:

+--------------+---------------------------------------+
| part         | assembly_step  |      finish_date     |
+--------------+----------+----------------------------+
| battery      | 1              |  01/22/2022 00:00:00 |
| battery      | 2              |  02/22/2022 00:00:00 |
| battery      | 3              |  03/25/2022 00:00:00 |
| bumper       | 1              |  01/22/2022 00:00:00 |
| bumper       | 2              |  02/22/2022 00:00:00 |
| bumper       | 3              |                      |
| bumper       | 4              |                      |
+--------------+----------------+----------------------+

Example Output:

+---------+-----------------+
| part    |  assembly_step  |
+---------+-----------------+
| bumper  |  3              |
| bumper  |  4              |
+---------+-----------------+

Explanation:

The bumpers in step 3 and 4 are the only item that remains unfinished as it lacks a recorded finish date.
