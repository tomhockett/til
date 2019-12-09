# #Tap

This helpful method enables you to “tap into” a method chain and perform some tangential function.  Here is the source code:

```ruby
class Object
  def tap
    yield self
    self
  end
end
```

This little method yields itself to the block and then returns the original self, after 'tapping' into the method chain.

We can take literal method calling:

```ruby
user = User.new
user.username = "tomhockett"
user.save!
```

And do something much more readable like this:

```ruby
user = User.new.tap do |u|
  u.username = "tomhockett"
  u.save!
end
```

It's clear what gets saved to the user variable; a clear progression of methods.

A more Rails-y example.  How do we build a full_name when there may-or-may-not be a middle name attribute?  We don't want an extra space if middle name doesn't exist.  `#tap` to the rescue!


```ruby
def full_name
  @full_name ||= ''.tap do |str|
    str << user.firstname
    str << " #{user.middlename}" if user.middlename
    str << " #{user.lastname}"
  end
end
```