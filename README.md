## Live Project: Analyzing User Behavior on Instagram

## Overview
This live project involves the analysis of a real-world dataset representing user behavior on Instagram. The project focuses on data cleaning and analysis using Python and MySQL. The process includes removing unwanted columns and renaming appropriate columns for improved analysis, followed by querying the dataset to extract insights into user engagement.

## Task 1: Data Cleaning for Comments
Data cleaning for comments is a critical step in enhancing the dataset's quality for analysis and modeling. This process involves removing irrelevant or redundant columns and ensuring that the column names are descriptive and consistent.

## Actions taken:

1) Removed unwanted columns.
2) Renamed columns for clarity and consistency.

## Task 2: Analysis of User Engagement on Instagram

### 1. Total Number of Users
SELECT COUNT(DISTINCT user_id) AS total_users
FROM comments;
Insight: The total number of unique users in the dataset provides an understanding of the user base.

### 2. Average Number of Comments per Post
SELECT post_id, AVG(comment_count) AS avg_comments_per_post
FROM posts
GROUP BY post_id;
Insight: Calculating the average number of comments per post helps in gauging the engagement level for each post.

### 3. Top 5 Users with the Highest Number of Posts
SELECT user_id, COUNT(*) AS post_count
FROM posts
GROUP BY user_id
ORDER BY post_count DESC
LIMIT 5;
Insight: Identifying the top users with the highest number of posts provides insights into active contributors.

### 4. Most Engaging Posts (Highest Likes and Comments)
SELECT post_id, (likes + comment_count) AS engagement_count
FROM posts
ORDER BY engagement_count DESC
LIMIT 5;
Insight: Discovering the most engaging posts based on likes and comments helps in understanding popular content.

### 5. Average Likes per User
SELECT user_id, AVG(likes) AS avg_likes_per_user
FROM posts
GROUP BY user_id;
Insight: Calculating the average likes per user provides insights into individual user popularity.

### 6. Users with High Comment Activity
SELECT user_id
FROM (
    SELECT user_id, COUNT(DISTINCT post_id) AS post_count
    FROM comments
    GROUP BY user_id
) AS user_comment_counts
WHERE post_count > (SELECT COUNT(DISTINCT post_id) * 0.5 FROM posts);
Insight: Identifying users who have commented on more than 50% of the posts helps in recognizing highly engaged users.

## Conclusion
The completion of this project involved effective data cleaning and insightful SQL queries to analyze user behavior on Instagram. The results provide valuable information for content creators, marketers, and businesses aiming to understand and optimize their strategies on the platform.
