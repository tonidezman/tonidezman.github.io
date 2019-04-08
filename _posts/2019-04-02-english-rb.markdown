---
layout: post
title:  "Nicer global_variable names with English.rb"
date:   2019-04-02 09:00:00 +0200
categories: Ruby
---

If you checkout what kind of global variables you have at your disposal you can use global_variables helper that does just that.

{% highlight ruby %}
global_variables # => [:$-0, :$\, :$:, :$-I, :$LOAD_PATH, :$", :$LOADED_FEATURES, :$-p, :$-l, :$@, :$!, :$-a, :$VERBOSE, :$-v, :$-w, :$-W, :$DEBUG, :$-d, :$0, :$PROGRAM_NAME, :$stdin, :$stdout, :$stderr, :$>, :$<, :$., :$FILENAME, :$-i, :$SAFE, :$*, :$_, :$~, :$;, :$-F, :$SiB, :$&, :$`, :$', :$+, :$=, :$KCODE, :$-K, :$?, :$$, :$,, :$/]
{% endhighlight %}

`$:` is not that self explanatory. Especially for the newcomer. That is why you can use `$LOAD_PATH` to improve readability of your code. `$:` and `$LOAD_PATH` give you back the same output.

But lets say that you wanted to use `$$` which gives you Ruby process id. You could write more readable global variable yourself or you could use build in `English.rb` file that lives inside your Ruby installation.

{% highlight ruby %}
require 'English'

global_variables # => [:$-0, :$\, :$:, :$-I, :$LOAD_PATH, :$", :$LOADED_FEATURES, :$-p, :$-l, :$@, :$!, :$ERROR_INFO, :$-a, :$VERBOSE, :$-v, :$-w, :$-W, :$DEBUG, :$-d, :$0, :$PROGRAM_NAME, :$OFS, :$ERROR_POSITION, :$FS, :$FIELD_SEPARATOR, :$ORS, :$OUTPUT_FIELD_SEPARATOR, :$RS, :$INPUT_RECORD_SEPARATOR, :$LAST_READ_LINE, :$OUTPUT_RECORD_SEPARATOR, :$INPUT_LINE_NUMBER, :$NR, :$PROCESS_ID, :$DEFAULT_OUTPUT, :$DEFAULT_INPUT, :$stdin, :$stdout, :$stderr, :$>, :$IGNORECASE, :$PID, :$MATCH, :$CHILD_STATUS, :$LAST_MATCH_INFO, :$LAST_PAREN_MATCH, :$ARGV, :$PREMATCH, :$POSTMATCH, :$<, :$., :$FILENAME, :$-i, :$SAFE, :$*, :$_, :$~, :$;, :$-F, :$SiB, :$&, :$`, :$', :$+, :$=, :$KCODE, :$-K, :$?, :$$, :$,, :$/]
{% endhighlight %}

And now you have `$PID` that gives you the same output that `$$`
