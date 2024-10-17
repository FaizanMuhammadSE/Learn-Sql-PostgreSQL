Lets build a like system

Liking system exists on many apps

## Use Cases

1. Each user can `like` a specific post a single time
2. A user should be able to `unlike` a post
3. Need to be able to figure out how many users like a post
4. Need to be able to list which users like a post
5. Something besides a post might need to be liked (comments)
6. We might want to think about `dislikes` or other kinds of reactions e.g. funny, confused

## What not to do

- Normally what you can think of having a `Users` table and a `Posts` table
- As user can like a post, so simply add a no. of `likes` column in `Posts` table
- It will left lot of our use-cases unsolved e.g
  - No way to make sure a user likes a post only once
  - No way to make sure a user can only _unlike_ a post if they have _liked_
  - No way to figure out which users like a particular post
  - No way to remove a like if a user gets deleted

## What to do

- As its many-to-many relationship between users and post likes
- For many-to-many relationshipt there is always a third table come into picture
- Third table named `Likes` will have a user_id and post_id
- Now we can easily many of the use-cases mentioned above
- To avoid user from liking same post multiple time, we can add unique constraint on user_id, post_id
- We can perform lot queries e.g.
  1. No. of likes on post with `id=3`
  2. Ids of top five most liked Posts
  3. Username of people who liked post with `id=3`
  4. URL of post that user with `id=5` liked
- To allow different type of reactions on posts, we would like to add a column named `type` in our third table which will hold the reaction value e.g. `angry` `like` `sad`, and definitely we should rename our third column from `Likes` to `Reactions`

#### Posts Table

| id  | content     |
| --- | ----------- |
| 1   | First post  |
| 2   | Second post |

#### Comments Table

| id  | post_id | content        |
| --- | ------- | -------------- |
| 1   | 1       | First comment  |
| 2   | 1       | Second comment |
| 3   | 2       | Third comment  |

#### Reactions Table

| id  | user_id | post_id | reaction |
| --- | ------- | ------- | -------- |
| 1   | 1       | 1       | like     |
| 2   | 2       | 1       | funny    |
| 3   | 1       | 2       | sad      |
| 4   | 3       | 3       | like     |

### Polymorphic Associations Table

Lets say user can like a post and **comment** as well, how will we upgrade our system
To represent polymorphic associations, we can design our tables as follows:

#### Posts Table

| id  | content     |
| --- | ----------- |
| 1   | First post  |
| 2   | Second post |

#### Comments Table

| id  | post_id | content        |
| --- | ------- | -------------- |
| 1   | 1       | First comment  |
| 2   | 1       | Second comment |
| 3   | 2       | Third comment  |

#### Reactions Table

| id  | user_id | liked_id | liked_type | reaction |
| --- | ------- | -------- | ---------- | -------- |
| 1   | 1       | 1        | post       | like     |
| 2   | 2       | 1        | comment    | funny    |
| 3   | 1       | 2        | post       | sad      |
| 4   | 3       | 3        | comment    | like     |

In the `Reactions` table:

- `liked_id` can be the `id` of either a post or a comment.
- `liked_type` specifies whether the `liked_id` refers to a post or a comment.

This setup allows users to react to both posts and comments using a single `Reactions` table.
**_Issue:_** we want able to set liked_id column as foreign key, because for foreign key we have to attach column with a single column but liked_id column contains ids of 2 tables. foreign key constaraints won't be applied here

### Polymorphic Associations Table Alternative Implementation (Recommended)

- We will be having 2 id columns in the `Reactions` table
- `post_id` and `comment_id` to point both posts and comments table separately.
- Now we can apply foreign key constraints

**_Issue:_** if there are multiple tables, then we will have to create multiple columns in reactions table to point them separately. so in such scenario prior approach will be suitable
