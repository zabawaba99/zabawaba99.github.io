---
layout: post
title:  "Snag"
categories: development
---

## TL;DR
---

Pretty neat tool that allows you to run any commands you want you
based off file system changes. <a href="https://github.com/Tonkpils/snag">Find it on Github</a>

---

A little while back [Leo Correa](http://leonardocorrea.com/) introduced
me to a neat tool called [glitch](https://github.com/levicook/glitch). It
allows you to automatically build, vet and test your go code as develop. I 
started using it on my personal projects at first and quickly made it part of
my workflow for any go proejct that I touch. 

Unfortunately I found myself still having to run some commands afterwards 
like `gofmt -l -s` and `golint .`. Leo and I began chatting about this and
decided to rewrite glitch mostly for some exposure on handling file
system events and to add in a few additional commands. Then [snag](https://github.com/Tonkpils/snag)
was born.

