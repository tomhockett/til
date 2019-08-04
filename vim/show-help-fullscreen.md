# Show help docs in fullscreen mode
When opening a help document in vim with `:help`, the documentation will load in a horizontal split screen with the docs truncated in the window above. Here's how we can view the docs fullscreen for a much better reading experience:

```
CTRL-w o 
```

* o for 'only mode'
* w for 'window'
* c for 'close'

Similarly, you can switch to the other window with `CTRL-w w` and close it with `CTRL-w c`, leaving you with just the help.

Alternatively, you could open the help window in a new tab: `:tab help foo`, and then use `:q` to close it.
