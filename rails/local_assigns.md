# local_assigns

This is a Rails view helper method that can be used to check whether this partial has been provided with local variables or not.

Here's a call to render for this partial:

```
<%= render "shared/header", { headline: => "Welcome", person: => person }%>
```

In `shared/header` view page:

```
Headline: <%= headline %>
First name: <%= person.first_name %>
```

You can check if these variables have been set or not:

```
<% if local_assigns.has_key? :headline %>
  Headline: <%= headline %>
<% end %>
```

Testing using `defined? headline` will not work.  This is an implementaion restriction.
