---
layout: post
title:  "Snag"
categories: development go
post_description: A tool for all your automated needs.
---

#### TL;DR

Neat tool that allows you to automagically run shell commands
when it detects a file change. <a href="https://github.com/Tonkpils/snag">Find it on Github</a>

---

A little while back [Leo Correa](http://leonardocorrea.com/) introduced
me to a neat tool called [glitch](https://github.com/levicook/glitch). It
allows you to automatically build, vet and test your go code as develop. I
started using it on my personal projects at first and quickly made it part of
my work-flow for any go project that I touch.

Unfortunately I found myself still having to run some commands afterwards
like `gofmt -l -s` and `golint .`. Leo and I began chatting about this and
decided to rewrite glitch mostly for some exposure on handling file
system events and to add in a few additional commands. Then [snag](https://github.com/Tonkpils/snag)
was born.

### Using Snag

Snag uses a `.snag.yml` file to know what files to watch and
what commands to run when they are changed. The file consist of
three sections: `script`, `ignore` and `verbose`

The **script** section allows you to specify a list of commands
that you want to execute. The entire list is executed whenever
any file in the same directory or subdirectories changes.
If one command fails (exits with anything but 0) no other command
will run.

The **ignore** section works just like a [gitignore](https://www.kernel.org/pub/software/scm/git/docs/gitignore.html), you can specify
files that you do not want snag to worry about. Any file/folder found in
this section will not cause the *script* section to run if modified.

The **verbose** section lets you see all the output of the commands that
are executing. By default, snag will only output a command's output if it fails.

**Putting it all together**

A `snag.yml` file looks something like

{% highlight yaml %}
script:
  - echo "hello world"
  - go test
ignore:
  - .git
  - my-binary
verbose: true
{% endhighlight %}

Running snag in the folder that contains this file will execute the directives as stated above

### Snag it!

You can find the project on [GitHub](https://github.com/Tonkpils/snag) and
download a version of snag in the [releases section](https://github.com/Tonkpils/snag/releases).

If you use [Homebrew](http://brew.sh/) as your package manager you can run

{% highlight sh %}
brew update && brew install snag
{% endhighlight %}

Any feedback and suggestions are greatly appreciated. Go give it a try!