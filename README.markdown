Using the Demo
==============

I have the following bash script which will switch from tag to tag.

```
git stash --include-untracked && git checkout -f "$1" > /dev/null
```

Demo Script
===========


Create Rails App
----------------

rails \_4.2.4\_ new blahblog\_

(note, the repo is actually in blahblog. I want to show Rails actually generating an app, but I want to use the one under source control.)

* Uncomment therubyracer
* get rid of Spring, which causes future steps to fail, with `spring stop`
* `bundle`

==== This is tag 0

* Start Server with `bin/rails server -b 0.0.0.0 -p 9125`
* Look, Rails is running. It's using WEBrick, which isn't good for production but works great for development. Even a blank app with no database is ready to go.

Hello World
-----------

* create a pages controller. Create pages#welcome. render text: 'hello world'
* in config/routes.rb, root to: 'pages#welcome'
* it works!

==== This is tag 1

Demostrate Gems / make It Pretty / Show Controller Flow
-------------------------------------------------------

* open Gemfile. Add `gem 'bootstrap-generators'`
* `bundle`
* `rails generate bootstrap:install`
* view hasn't changed.
* move Hello World to view.
* add some silly auth

==== This is tag 2

Create Posts
------------

* `bin/rails generate scaffold posts title body:text`
* load /posts
* see error about migration
* Thank you for providing me with instructions, I think I will do what you suggest.
* copy and paste migration command
* show posts#index
* add validations to the Post model
* add 4 posts.
* delete one.
* add validations to Post model

* model names are always singular.
* their table names are always plural.
* view directories are always plural.

==== This is tag 3

Some basic work in views
------------------------

* table becomes div with class="panel panel-default panel-body"
* add "Posts" to the menu in app/views/layouts/application.html.erb
* demonstrate mobile view for free.


* look at all the code I'm not writing. Configuration I'm not doing.

==== This is tag 4

A bit more view stuff
---------------------

* abstract panels from index into posts/_post
* show that posts#index is still working
* Change posts#show
  * title is in the page header.
  * add a `label label-warning` if not published
  * `simple_format` the body
  * `time_ago_in_words` for `created_at`

==== This is tag 5

Comments - AR Relationships
---------------------------

* `bin/rails g scaffold comments post_id:integer author body:text`
* app/models/comment.rb: `belongs_to :post`
* app/models/post.rb: `has_many :comments`
* copy form from `comments/_form` to `posts/_comment_form`
* render :partial => 'posts/comment_form'
* post_id should be hidden
* add a comment. Goes to comments#show... not a great experience. Change comments controller.
* Create a posts partial.
* create another one. Better!
* add a comment count to posts#index

==== This is tag 6


* Let's say someone wants to syndicate our blog post after the third entry... hooray!
* show posts.json
* add comments by going to `posts/_post.json.jbuilder` and adding `json.comments post.comments`
* Maybe they want RSS. Find the Wikipedia RSS feed and create app/views/posts/index.rss.erb

==== This is tag 7
