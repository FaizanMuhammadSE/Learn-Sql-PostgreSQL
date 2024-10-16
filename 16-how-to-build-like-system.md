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
