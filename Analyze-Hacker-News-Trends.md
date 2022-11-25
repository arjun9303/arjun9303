--Q. find the total score of all the stories. (A) we need to pinpoint the users who have accumulated a lot of points across their stories.Find the individual users who have gotten combined scores of more than 200, and their combined scores. 
-- SELECT user, SUM(score) AS Total_Score FROM hacker_news
  GROUP BY user HAVING SUM(score)>200
  ORDER BY Total_Score DESC;

--Q.  we want to add these users’ scores together and divide by the total to get the percentage.
--SELECT (517 + 309 + 304 + 282) / 6366.0;


--Q. The url of the video is: https://www.youtube.com/watch?v=dQw4w9WgXcQ How many times has each offending user posted this link?
--SELECT url, COUNT(url) FROM hacker_news
--WHERE url LIKE "https://www.youtube.com/watch?v=dQw4w9WgXcQ";

/*--Q. Which sites feed Hacker News?
SELECT CASE
  WHEN url LIKE "%github.com%" THEN 'Github'
  WHEN url LIKE "%medium.com%" THEN 'Medium'
  WHEN url LIKE "%nytimes.com%" THEN 'New York Times' 
  ELSE 'other' 
END AS 'Source',
COUNT(*)
FROM hacker_news
GROUP BY Source;*/

--Let’s write a query that returns three columns:
--1. The hours of the timestamp
--2. The average score for each hour
--3. The count of stories for each hour
SELECT STRFTIME('%H', timestamp) AS time_hourly,
ROUND(AVG(score),2) AS avg_score, 
COUNT(title) FROM hacker_news 
WHERE timestamp IS NOT NULL GROUP BY time_hourly ORDER BY time_hourly ASC;



