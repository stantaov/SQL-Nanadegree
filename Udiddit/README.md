<h1>Project Description</h1>

<p>
Udiddit, a social news aggregation, web content rating, and discussion website, is currently using a risky and unreliable Postgres database schema to store the forum posts, discussions, and votes made by their users about different topics.</p>
<p>The schema allows posts to be created by registered users on certain topics, and can include a URL or a text content. It also allows registered users to cast an upvote (like) or downvote (dislike) for any forum post that has been created. In addition to this, the schema also allows registered users to add comments on posts.</p>

After investigating both table schemas I recommend applying following changes:

For bad_posts table
- It is not a good practice to use TEXT data type since it can use up to 1Gb of data
per record. So, it is advisable to use VARCHAR with a limited number of characters
for text_content field
- Upvotes field should have INTEGER data type, currently it has TEXT data type with
user names who upvoted given post
- Downvotes field should have INTEGER data type, currently it has TEXT data type
with user names who downvoted given post For bad_comments table
- Username field should be UNIQUE and NOT NULL
- Text_content should be changed to VARCHAR with limited number of characters
- Post_id field should be UNIQUE and NOT NULL
