## Recreating Our Social Media App

### Adding a User Model

Today's Goal is to incorporate a User model into your social media apps. 

**Step 1** - Create a migration to create a users table (as always, refer to Fwitter as a guide). The user should have columns for username and email. 

**Step 2** - Create a User model that inherits from ActiveRecord::Base. Remember, if you have a table called users, you need a model called User. 

**Step 3** - It's your content's job to keep track of which user it belongs to, but it needs to keep track by the user's id, not the username. Create another migration that removes the username column from your content and adds a column called user_id (again, let Fwitter be your guide) Run the migrations using `rake db:migrate`

**Step 4** - Your content model no longer responds to a method called `username`. Instead, it responds to a method called `user` which returns the user object. That user object responds to a method called `username`. Update your views so that you're calling `content.user.username` instead of `content.username`. 

**Step 5** - Any content that we created before won't have a user_id associated with it, which will cause errors when running our application. We can fix this by updating the data using tux. Boot up `tux` in the terminal and destory your previously created content like so: `Tweet.destroy_all`

**Step 6** - Create a form to create new users. Setup the necessary controller actions so that you can add Users to your database - it should look similar to the way you create new content. 

**Step 7** -  Modify the way your content is created. This will happen in two steps: 
	* First, update the form so that a user enters their id number instead of their username .
	* In the controller, new content should no longer be created with a username. Instead, it should be created with a user_id. 

## Bonus Challenges

+ It's kind of lame that a user has to memorize their id number to be able to post content. Update this for a better user experience by adding a drop-down menu of every user in our database. The drop-down should display their username, but the value should be their user_id. 
+ Add another model/relationship to your app to expand functionality. Some ideas:
	* Comments
	* Hashtags
	* Retweets
	+ Think carefully about the relationship between hashtags and tweets.



