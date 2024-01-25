## Research Assistant for University of Iowa's department of Management and Entrepreneurship: Reddit Scraper project

### Summary:
I worked under the leadership of Dr. Jennifer Nahrgang and Dr. Emily Campion in the Department of Management and Entrepreneurship at the University of Iowa to conduct their data collection for my Spring 2023 Research Assistant position. I utilized libraries including Python Reddit Wrapper Libraries (praw, pushshift_py) and applied text mining, data cleansing, and supervised machine learning techniques (k-means clustering), to scrape over 150,000 rows of subreddit data from two subreddits (r/overemployed & r/onlyfansadvice) in 2022.

Using PyCharm, I scraped all of the submissions (subreddit posts) and subsequent comments from the period January 2022 - December 2022 for each subreddit. Following this initial scraping, I used Jupyter Notebooks to clean the data and create new columns in the dataframes to include information on if a post received comments (see 'InitialCleaning.ipynb').

Overall, my work streamlined the process for Dr. Nahrgang and Dr. Campion in data collection for their research projects. I was able to gain skills in API calls and use my self-starter mentality, critical thinking skills, and effective communication with the team to produce an exceptional outcome.

### Relevant Files:
#### InitialCleaning.ipynb
- The data cleansing code

#### 7clusters_Text_Clustering_kMeans_Submissions.html
- Following scraping and cleansing of data, I applied k-means clustering on the submissions data for r/overemployed. These results were used to aid Dr. Nahrgang in data exploration as distinct topics being discussed were grouped together.

- The obtained data followed the following structure:
#### submissions.csv

- Each row is a submission of a specific subreddit and `id` field is unique across the dataset (PK).

| Column name | Description                          | Example                                                                |
|-------------|--------------------------------------|------------------------------------------------------------------------|
| subreddit   | Name of the subreddit                | MTB                                                                    |
| id          | Unique identifier of the submission  | lhr2bo                                                                 |
| created_utc | UTC when submission was created      | 1613068060                                                             |
| title       | Title of the submission              | Must ride So...                                                        |
| selftext    | Text off the submission              | What are the best trails to ride in...                                 |
| full_link   | Reddit unique link to the submission | https://www.reddit.com/r/MTB/comments/lhr2bo/must_ride_so_cali_trails/ |

#### comments.csv

- Each row is a comment under a submission of a specific subreddit and `id` field is unique across the dataset (PK).

| Column name | Description                          | Example                                                                          |
|-------------|--------------------------------------|----------------------------------------------------------------------------------|
| subreddit   | Name of the subreddit                | News                                                                             |
| id          | Unique identifier of the comment     | gmz45xo                                                                          |
| submission_id | Id of the comment main submission  | lhr2bo                                                                          |
| body        | Text of the comment                  | We're past the point...                                                          |
| created_utc | UTC when comment was created         | 1613072734                                                                       |
| parent_id   | Id of the parent in a tree structure | t3_lhssi4                                                                        |
| permalink   | Reddit unique link to the comment    | /r/news/comments/lhssi4/air_force_wants_to_know_if_key_pacific_airfield/gmz45xo/ |

---

## :book: Glossary

- _subreddit_: section of reddit website focused on a particular topic

- _submission_: the post that appear in each subreddit. When you open a subreddit page, all the posts you see. Each submission has a tree of _
  comments_

- _comment_: text wrote by a reddit user under a _submission_ inside a _subreddit_
    - The main goal of this repository is to gather the _comments_ belong to the _subreddit_

## :writing_hand: Notes and Q&A

- Under the hood the script use [pushshift](https://pushshift.io/api-parameters/) to gather submissions id,
  and [praw](https://praw.readthedocs.io/en/latest/)
  for collect the submissions comments
    - With this approach we require fewer data to [pushshift](https://pushshift.io/api-parameters/)
    - Due to the usage of [praw](https://praw.readthedocs.io/en/latest/) API, the reddit credentials are required
- More info about the `subreddit_downloader.py` script under the `--help` command:
- Other packages:
    - [psaw](https://github.com/dmarx/psaw): Python Pushshift.io API Wrapper
