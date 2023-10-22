---
title: Ruby on Rails Scopes
date: 2023-10-05
tags: ['Ruby on Rails', '', 'Rails Scopes']
---

# Ruby on Rails Scopes

## What is scope in Rails?

![Alt text](/images/ruby-on-rails-scopes.png)

Scopes in Rails are special methods to run SQL queries that you can build in any rails model. A
scope will always return an ActiveRecord::Relation object, even if the conditional evaluates to
false , whereas a class method, will return nil. we frequently run similar queries in our rails
console to query our database and also understand the structure of the result we are receiving
before going further with the development of our applications.

Why use Scopes? & why is it useful

A use case for scopes is often for filtering by status, date, date ranges, ordering, groupings, and
more. Compared to class methods, scope methods are incredibly fast and quite easy to return the
desired result in fraction of time.

Scopes help you D.R.Y out your active record calls and also keep your codes organized. Scopes make
it easy to find the records you need at a particular time.

Lets start with the basic, We’ll use a sample model named Book to illustrate what scopes allow you
to do.

On your homepage, you only want to show published books of course. So in your action, you would use
the following code to ensure that.

```js
Class Book < ActiveRecord::Base
  scope :published, -> { where(:published => true) }
end
```

# This retuns ActiveRecord::Relation object

Then in our controller or views, we can return the newly scoped objects.

```ruby
class BooksController < ApplicationContrpller
 def index
   @books = Book.published
 end
end
```

Taking arguments.

scopes can also receive parameters, let’s see how we can create a scope to get all books written by
a specific author.

```ruby
class Book < ActiveRecord::Base
 scope :author_name, -> (name) { where(:authorName => name) }
end
```

Using conditional with scopes.

The scope named available, in the code block is a typical example of how to use conditional with
scopes.

```ruby
class Book < ActiveRecord::Base
 scope :available, -> (bool) { where("available = ?", bool) if bool.present? }
end
```

Chaining

Scopes are extremely powerful due to their ability to be chained together. Think of them as a chain
links

```ruby
class BooksController < ApplicationContrpller
 def index
   # return all available & published books.
   @books = Book.published.available
 end
end
```

Summary

It’s always a good idea to use scopes for selecting, sorting, joining or filtering data through your
database, and then you can use class methods to chain those scopes, or even write more complex
logic.

This is very important to note that the scope is intended to return an ActiveRecord::Relation object
which is composable with other scopes. In short scopes should be chainable.

Hope this article helped you understand the ActiveRecord Scoping method and its uses.

Thank you for reading! ❤️
