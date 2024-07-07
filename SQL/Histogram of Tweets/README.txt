Solution
===================================================================================================

WITH subq AS 
(
SELECT COUNT( tweet_id) AS tweet_bucket, user_id AS user_num
FROM tweets
WHERE EXTRACT(year FROM tweet_date)=2022
GROUP BY user_id
)

SELECT tweet_bucket, COUNT(user_num) AS users_num
FROM subq
GROUP BY tweet_bucket;


===================================================================================================
Problem
===================================================================================================

Assume you're given a table of Twitter tweet data, and write a query to obtain a histogram of tweets posted per user in 2022. Output the tweet count per user as the bucket and the number of Twitter users who fall into that bucket.

In other words, group the users by the number of tweets they posted in 2022 and count the number of users in each group.

Table: tweets

+-------------+-----------+
| Column Name | Type      |
+-------------+-----------+
| tweet_id    | int       |
| user_id     | int       |
| msg         | string    |
| tweet_date  | timestamp |
+-------------+-----------+

Example Input of tweets table:

+----------------+----------+---------------------------------------------------------------------+---------------------+
|    tweet_id    |  user_id |                                      msg                            | tweet_date          |
+----------------+----------+---------------------------------------------------------------------+---------------------+
| 214252         | 111      | I Am considering taking Tesla private at $420. Funding secured.     | 12/30/2021 00:00:00 |
| 739252         | 111      | Despite the constant negative press conference                      | 01/01/2022 00:00:00 |
| 846402         | 111      | Following @NickSinghTech on Twitter changed my life!                | 02/14/2022 00:00:00 |
| 241425         | 254      | If the salary is so competitive why won’t you tell me what it is?   | 03/01/2022 00:00:00 |
| 231574         | 148      | I no longer have a manager. I can't be managed                      | 03/23/2022 00:00:00 |
+----------------+----------+---------------------------------------------------------------------+---------------------+


Example Output:

+--------------+------------+
| tweet_bucket | users_num  |
+--------------+------------+
| 1            | 2          |
| 2            | 1          |
+--------------+------------+
 
Explanation:

Based on the example output, there are two users who posted only one tweet in 2022, and one user who posted two tweets in 2022. The query groups the users by the number of tweets they posted and displays the number of users in each group.

