### Part 6: Use the new dependency {#part-6-use-the-new-dependency}

Now we’re ready to put the new dependency (lodash) to good use.

1.  In Sublime, copy or type the following into **index.js**, then save again:

| var _ = require(&#039;lodash&#039;); |
| --- |

1.  On the command line, type: **browserify index.js &gt; bundle.js**
2.  Refresh (or open again) index.html in your browser.

Your rendered HTML file should look like this: