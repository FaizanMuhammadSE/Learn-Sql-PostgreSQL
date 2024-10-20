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

- A user can leverage mentioning in many posts, and a post can have many users mentioned
  - so its like many-to-many relationship
  - for many-to-many we always go for third table
- Table will be named as _mentions_ and it will have following properties
  - `id` `user_id` `post_id` `x_coordinate` `y-coordinate`
  - coordiantes will tell the exact location in photo
  - As we have 2 types of mentions `caption_mention` `photo_mention` both will be covered by this single table, for `caption_mention` x,y coordinates will have NULL value
