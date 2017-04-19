================= Challenge 1 =================

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

================= Challenge 2 (Optional) =================

** Extending "label" **

When a form entry creates an invalid object, one useful design approach is to show validation errors inside the form's field labels, rather than in a big container above or below the form.

So if we have a form for model "Book," a new Book record with an invalid "author" field might expand the "author" label to say "author cannot be blank."  

This can take a bit of repetition to program into many fields and forms, so it's ripe for automation.

One way to do this would be to extend the Rails "label" method to present different styling (say, an 'error' font class) and an appropriate validation message (e.g. "FIELD has too many characters") if the object and field need it.  You could even add an optional flag like ":inline_errors" to only show errors this way on certain forms, or extend it into a separate method altogether, e.g. "label_with_inline_errors."

================= Challenge 3 (Optional) =================

** Adding "grid()" **

Another common front-end task is to display a bunch of records (and their particular visualizations/elements) in a NxM grid.

One page might need 12 BlogEntry records sorted into 3 columns, with a detailed rundown of each BlogEntry inside its individual window.  On another page you might have 30 CalendarDays to show, but 7 columns worth of space to show them in, and require little more than the weekday name (Monday, Tuesday, etc.) in each cell.  

You could create a grid() helper function to speed this process along.  grid() can take a collection of records and a number of columns (realistically, somewhere between 2 and 8) to break them into, and generate the nested divs or tables you need. 

Similar to Rails' "form_for()," it should be able to sandwich an arbitrary block of irb to render into each cell of the grid.  So each cell would house the same irb code, and render it with the appropriate BlogEntry/CalendarDay/X object.
