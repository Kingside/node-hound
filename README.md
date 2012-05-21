hound - directory tree watcher for node.js
=============================================

Cross platform directory tree watcher that works, even on Windows
-----------------------------------------------------------------

I've recently started some node.js projects, and have been very unhappy with the
results.  Many work well, but aren't cross platform.  hound was written to
create a simple directory tree watcher, with lots of tests, that actually works.
Even on Windows.

hound is designed to be very simple, fast and reliable.  There are no runtime
dependencies outside of the standard node.js libraries.  There is a development
dependency on [Jasmine](http://pivotal.github.com/jasmine/), which is required
to run the tests.

Installation
------------

Install using npm:

```
npm install hound
```

Usage
-----

```javascript
hound = require('hound')

// Create a directory tree watcher
watcher = hound.watch('/tmp')

// Create a file watcher
watcher = hound.watch('/tmp/file.txt')

// Add callbacks for file and directory events
watcher.on('create', function(file, stats) {
  console.log(file + ' was created')
})
watcher.on('change', function(file, stats) {
  console.log(file + ' was changed')
})
watcher.on('delete', function(file) {
  console.log(file + ' was deleted')
})

// Unwatch specific files or directories
watcher.unwatch('/tmp/another_file')

// Unwatch all watched files and directories
watcher.clear()
```

Testing
-------

To run the tests using your global Jasmine binary:

```
jasmine-node spec
```

To run the tests using your local Jasmine binary in node_modules:

```
node_modules/.bin/jasmine-node spec
```

The tests work on actual directory trees that are generated in the tmp
directory.
