---
layout: post
title:      "My own Instagram!!"
date:       2020-11-08 21:53:59 -0500
permalink:  my_own_instagram
---


For my Rails project, I have built a clone of Instagram. It has been an exciting as well as daunting experience! It was hard to clone a professional-looking website in such a short period. So, I have built a basic version with the most common features – like, comment, post, and follow. The app has five models: User, Post, Comment, Like, and Follower. The hardest part was designing the database tables and building the like and follow feature. I knew I’ll need a user, a post, and a comment model. But I was not sure how I was going to associate a like and comment model with them. After many iterations, my models finally look like this. 


```
Class Comment < ApplicationRecord

  belongs_to :user
  belongs_to :post

  validates_presence_of :comment, :user_id, :post_id

  after_create :increase_post_comment_counter
  after_destroy :decrease_post_comment_counter
	
end


class User < ApplicationRecord

  has_many :posts, dependent: :destroy
  has_many :comments, dependent: :destroy
  has_many :likes, dependent: :destroy
  has_many :posts, through: :comments
  has_many :followers, class_name: :Follower, foreign_key: :following_id, dependent: :destroy
  has_many :followings, class_name: :Follower, foreign_key: :follower_id, dependent: :destroy
	
  end

class Follower < ApplicationRecord

  validates_uniqueness_of :follower_id, scope: :following_id
  belongs_to :followee, class_name: :User, foreign_key: :following_id
  belongs_to :follower, class_name: :User, foreign_key: :follower_id
	
end

class Like < ApplicationRecord

  belongs_to :post
  belongs_to :user

  validates_uniqueness_of :post_id, scope: :user_id
  after_create :increase_post_like_counter
  after_destroy :decrease_post_like_counter
	
end

class Post < ApplicationRecord

  belongs_to :user
  has_many :likes, dependent: :destroy
  has_many :comments, dependent: :destroy
  has_many :users, through: :comments

end

```

The trickiest one was the Follower model because it had two attributes but both of them belonged to the User class. So, if I wanted to see a list of followers of a user, I could not call user.followers or user.followees. The solution I found was to use foreign_key and class_name methods. I named the following_id as followee, as a result when a user.followees is called, it will give the followees ids. The same goes for user.followers. Moreover, to keep track of the likes in a post, I created two counter methods that will increase or decrease the number of likes accordingly. When a user likes a post, it will fire two SQL queries, one will either create or delete alike and the other would increase or decrease the counter variable. 

This project is a huge stepping stone for me. I look forward to learning JavaScript and give my project a beautiful, solid front-end! 


