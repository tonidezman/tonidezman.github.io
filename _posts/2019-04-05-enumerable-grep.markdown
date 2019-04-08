---
layout: post
title:  "Enumerable grep method"
date:   2019-04-05 09:00:00 +0200
categories: Ruby
---

If you are debugging something in your `irb` or `pry` REPL and you get back an array with a lot of values you can either search every element or you can use `grep` method.

Our mission in this blog post is that we want to find find every key that contains RBENV in the ENV hash

Let's look what ENV hash gives us back
{% highlight ruby %}
ENV.keys # => ["RBENV_VERSION", "VSCODE_CLI", "LDFLAGS", "AWS_HOME", "TERM_PROGRAM", "VSCODE_NODE_CACHED_DATA_DIR", "TERM", "SHELL", "AMD_ENTRYPOINT", "CPPFLAGS", "TMPDIR", "Apple_PubSub_Socket_Render", "TERM_PROGRAM_VERSION", "TERM_SESSION_ID", "ZSH", "OBJC_DISABLE_INITIALIZE_FORK_SAFETY", "ZSH_TMUX_TERM", "USER", "COMMAND_MODE", "RBENV_ROOT", "VSCODE_PREVENT_FOREIGN_INSPECT", "_ZSH_TMUX_FIXED_CONFIG", "SSH_AUTH_SOCK", "__CF_USER_TEXT_ENCODING", "VSCODE_LOG_STACK", "FZF_DEFAULT_OPTS", "PAGER", "RBENV_HOOK_PATH", "ELECTRON_RUN_AS_NODE", "TMUX", "LSCOLORS", "VSCODE_LOGS", "PATH", "WALLABY_PRODUCTION", "PWD", "VSCODE_HANDLES_UNCAUGHT_ERRORS", "ELECTRON_NO_ATTACH_CONSOLE", "EDITOR", "LANG", "ITERM_PROFILE", "TMUX_PANE", "XPC_FLAGS", "RBENV_SHELL", "XPC_SERVICE_NAME", "COLORFGBG", "SHLVL", "HOME", "PIPE_LOGGING", "APPLICATION_INSIGHTS_NO_DIAGNOSTIC_CHANNEL", "VSCODE_IPC_HOOK_EXTHOST", "VSCODE_NLS_CONFIG", "RBENV_DIR", "BUNDLER_EDITOR", "ITERM_SESSION_ID", "LESS", "LOGNAME", "LC_CTYPE", ...
{% endhighlight %}

How many keys do we get back?
{% highlight ruby %}
ENV.keys.count # => 68
{% endhighlight %}

It gives us a lot of stuff right ☺️. Lets filter out this a little bit.
{% highlight ruby %}
ENV.keys.grep /RBENV/ # => ["RBENV_VERSION", "RBENV_ROOT", "RBENV_HOOK_PATH", "RBENV_SHELL", "RBENV_DIR"]
{% endhighlight %}

Much better.
{% highlight ruby %}
ENV.keys.grep(/RBENV/).count # => 5
{% endhighlight %}
