In Rails version 3+, sketch out a new blog project with three interrelated models:  

**Author**, **Post**, and **Comment** 

The project itself needn't be supplied in detail.  Views and controller code are not necessary, so long as the model relations and the **Author.trending** scope are fleshed out in accordance with the instructions below.

=================

Authors write blog Posts, and their readers can leave anonymous Comments on each Post.

#### Author.rb

Authors have a name (string).

One Author can have many Posts.

#### Post.rb

Posts have a subject (string), a body (text), and a creation date.

Each Post associates with only one Author.

Each Post can have many Comments left on it by the internet at large.

#### Comment.rb

Comments have a body (text), and a creation date.

Each Comment is associated with only one Post.

#### Author.trending

Now, with these models in mind, write an **Author.trending** scope which satisfies the following: 

.trending is a way of measuring which Authors have earned the most Comments in the last week.

.trending returns Authors, sorted (descending) by the number of total Comments left in the last 7 days on all the Author's Posts

.trending does not return any Authors who have garnered no Comments in the last 7 days.

.trending doesn't care about the ages of the Posts themselves.  If a Post is more than 7 days old, but has new Comments, those Comments add to the Author's total.

Some considerations:

-- Write some basic tests for the Author.trending scope.  What conditions or edge cases might you use to ensure it's working correctly?

-- Can you optimize this .trending query?  How might you do this while maintaining legible Arel? 

=================

Please submit your examples to a separate branch in this repository.
