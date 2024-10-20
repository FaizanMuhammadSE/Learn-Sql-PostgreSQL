To add Post description, we will add a description column in post
To save location of photo, we will add 2 more columns longitude and latitude
To handle mention functionality we will follow following approach where user can mention other users in his post **(either in caption or in photo)**

### Use Cases

1. Highlighted text doesn't necessaryliy meant that we need to store something in the database
2. Mobile app could in charge of highlighting anything that looks like a mention
3. Need to show a list of posts a user was mentioned in
4. Need to show a list of the most-often mentioned users?
5. Need to notify a user when they have been mentioned

#### Approaches

##### First Approach

- A user can leverage mentioning in many posts, and a post can have many users mentioned
  - so its like many-to-many relationship
  - for many-to-many we always go for third table
- Table will be named as _mentions_ and it will have following properties
  - `id` `user_id` `post_id` `x_coordinate` `y-coordinate`
  - coordiantes will tell the exact location in photo
  - As we have 2 types of mentions `caption_mention` `photo_mention` both will be covered by this single table, for `caption_mention` x,y coordinates will have NULL value

###### Users Table

| id  | username | email             |
| --- | -------- | ----------------- |
| 1   | user1    | user1@example.com |
| 2   | user2    | user2@example.com |
| 3   | user3    | user3@example.com |
| 4   | user4    | user4@example.com |

###### Posts Table

| id  | user_id | content       | longitude | latitude  |
| --- | ------- | ------------- | --------- | --------- |
| 1   | 1       | Post by user1 | 40.7128   | -74.0060  |
| 2   | 2       | Post by user2 | 34.0522   | -118.2437 |
| 3   | 3       | Post by user3 | 51.5074   | -0.1278   |
| 4   | 4       | Post by user4 | 48.8566   | 2.3522    |

###### Mention Table

| id  | user_id | post_id | x_coordinate | y_coordinate |
| --- | ------- | ------- | ------------ | ------------ |
| 1   | 1       | 101     | NULL         | NULL         |
| 2   | 2       | 102     | 150.5        | 200.75       |
| 3   | 3       | 103     | NULL         | NULL         |
| 4   | 4       | 104     | 300.0        | 400.0        |

##### Second Approach

- We can create separate tables for both caption_mentioning and photo_mentioning
- This approach will be suitable if we think
  - data for either caption or photos going to be changed in future
  - Either `caption_mention` or `photo_mention` is going to be used frequently than other, so we can separate tables to perform optimizations on frequently used table
