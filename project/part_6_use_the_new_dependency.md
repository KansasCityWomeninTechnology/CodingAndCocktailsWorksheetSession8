### Part 6: Use the new dependency {#part-6-use-the-new-dependency}

Now we’re ready to put the new dependency (lodash) to good use.

1.  In Sublime, copy or type the following into **index.js**, then save again:

        var _ = require('lodash');
        var wine = "I like red wine"
        var h4Heading = document.querySelector('h4');
        h4Heading.textContent = _.replace(wine, 'red', 'white');

1.  On the command line, type: ``browserify index.js > bundle.js``
2.  Refresh (or open again) **index.html** in your browser.

Your rendered HTML file should look like this:
![](../images/14.png)