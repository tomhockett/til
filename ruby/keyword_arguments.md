# Ruby Keyword Arguments

In Ruby 1.9, we could take a hash as a parameter and set a default like this:

```
  def person(params = {})
    user = params.fetch(:name, 'default')
    puts user
  end

  person # => 'default'
  person(name: 'Tom') # => 'Tom'
```

Ruby 2.0 introduced support for keyword arguments:

```
  def person(name: 'default')
    puts name
  end

  person # => 'default'
  person(name: 'Tom') # => 'Tom'
```

## Required Keyword Arguments

This came in version 2.1:

```
  def person(name:)
    puts name
  end

  person # => ArgumentError: missing keyword: name
  person(name: 'Tom') # => 'Tom'
```

If the argument is missing, Ruby raises an `ArgumentError`

## What can keyword arguments do for me?

1. Create clear code:

```
  def total_of_what_exactly(subtotal, tax, discount)
    (subtotal + tax) - discount
  end

  total_of_what_exactly(100, 10, 5) # => 105
```

This could be confusing because we don't know (as a reader) what those numbers mean without looking at the code.  By using keyword arguments, it's explicit what is happening:

```
  def total_of_numbers(subtotal:, tax:, discount:)
    (subtotal + tax) - discount
  end

  total_of_numbers(subtotal: 100, tax: 10, discount: 5) # => 105
```

2. Switch the order of arguments without affecting the behavior of the method:

```
  total_of_numbers(tax: 10, discount: 5, subtotal: 100) # => 105
```

3. Avoid connascence of position:

>Connascence between two software components A and B means either 1) that you can postulate some change to A that would require B to be changed (or at least carefully checked) in order to preserve overall correctness, or 2) that you can postulate some change that would require both A and B to be changed together in order to preserve overall correctness. - Meilir Page-Jones, [What Every Programmer Should Know About Object-Oriented Design](https://www.amazon.com/Every-Programmer-Should-Object-Oriented-Design/dp/0932633315)

If we decide to change the order of arguments in total_of_what_exactly, we will have to change the order of every method or call that uses that method.  Using Keyword Arguments, we can freely change the order of arguments without affecting the rest of the code.

