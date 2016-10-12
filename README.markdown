Using the Demo
==============

I have the following bash script which will switch from tag to tag.

```
git stash --include-untracked && git checkout -f "$1" > /dev/null
```

Demo Script
===========

rails \_4.2.4\_ new blahblog\_

(note, the repo is actually in blahblog. I want to show Rails actually generating an app, but I want to use the one under source control.)

* Uncomment therubyracer
* get rid of Spring, which causes future steps to fail, with `spring stop`
* `bundle`

==== This is tag 1

* Start Server with `bin/rails server -b 0.0.0.0 -p 9125`
* Look, Rails is running. It's using WEBrick, which isn't good for production but works great for development. Even a blank app with no database is ready to go.
* open Gemfile. Add `gem 'bootstrap-generators'`
* `bundle`
* `rails generate bootstrap:install`
* spring stop # just in case

==== This is tag 2

* `bin/rails generate scaffold posts title body:text`
* load /posts
* see error about migration
* Thank you for providing me with instructions, I think I will do what you suggest.
* copy and paste migration command
* show posts#index
* add 4 posts.
* delete one.

==== This is tag 3

Make index look more like a blog:
* table becomes div with class="panel panel-default panel-body"
* add "Posts" to the menu in app/views/layouts/application.html.erb
* demonstrate mobile view for free.

==== This is tag 4

* Let's say someone wants to syndicate our blog post after the third entry... hooray!
* show posts.json
* Maybe they want RSS. Find the Wikipedia RSS feed and create app/views/posts/index.rss.erb

==== This is tag 5

* abstract panels from index into posts/_post
* show that posts#index is still working
* add that to posts#show

==== This is tag 6

* `bin/rails g scaffold comments post_id:integer author body:text`
* app/models/comment.rb: `belongs_to :post`
* app/models/post.rb: `has_many :comments`
* copy form from scaffold to posts#show.
* post_id should be hidden.
* add a comment. Goes to comments#show... not a great experience.
* change it to redirect to the post.
* create another one. Better!

==== This is tag 7

