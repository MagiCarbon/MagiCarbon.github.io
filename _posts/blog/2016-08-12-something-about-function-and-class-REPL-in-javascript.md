---
layout: post
categories: blog
share: true
comments: true
title: something about function and class REPL in javascript
excerpt: es6 class function play in REPL
date: '2016-08-12T18:11:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [javascript, prototype, __proto__]
author: MC
hidelogo: true
---

<figure>
    <a href="/images/post/blog/2016/08-12-something-about-function-and-class-REPL-in-javascript.png"><img src="/images/post/blog/2016/08-12-something-about-function-and-class-REPL-in-javascript.png" alt="Code In ST3" class="center"/></a>
</figure>

## REPL

```
$ node
> function ClassA() { this.value = 'a'; }
undefined
>
> class ClassB { constructor() { this.value = 'b'; } }
[Function: ClassB]
> ClassA // [Function: ClassA]
[Function: ClassA]
>
> ClassB // [Function: ClassB]
[Function: ClassB]
>
> let a = new ClassA();
undefined
> let b = new ClassB();
undefined
>
> ClassA.prototype.echo = function() { return this.value; };
[Function]
>
> a.echo(); // 'a'
'a'
>
> b.echo(); // error
TypeError: b.echo is not a function
    at repl:1:3
    at sigintHandlersWrap (vm.js:32:31)
    at sigintHandlersWrap (vm.js:96:12)
    at ContextifyScript.Script.runInContext (vm.js:31:12)
    at REPLServer.defaultEval (repl.js:308:29)
    at bound (domain.js:280:14)
    at REPLServer.runBound [as eval] (domain.js:293:12)
    at REPLServer.<anonymous> (repl.js:477:10)
    at emitOne (events.js:101:20)
    at REPLServer.emit (events.js:188:7)
>
> ClassB.prototype.echo = function() { return this.value; }
[Function]
>
> b.echo(); // 'b'
'b'
>
> ClassA.prototype.echo === ClassB.prototype.echo; // false
false
>
> a.__proto__.echo = function() { return this.value + 'c'; };
[Function]
>
> a.echo(); // 'ac'
'ac'
>
> b.__proto__.echo = ClassA.prototype.echo;
[Function]
>
> b.echo(); // 'bc'
'bc'
>
> ClassA.prototype.echo === ClassB.prototype.echo; // true
true
>
```

**plain**

function ClassA() { this.value = 'a'; }

class ClassB { constructor() { this.value = 'b'; } }
ClassA // [Function: ClassA]

ClassB // [Function: ClassB]

let a = new ClassA();
let b = new ClassB();

ClassA.prototype.echo = function() { return this.value; };

a.echo(); // 'a'

b.echo(); // error

ClassB.prototype.echo = function() { return this.value; }

b.echo(); // 'b'

ClassA.prototype.echo === ClassB.prototype.echo; // false

a.__proto__.echo = function() { return this.value + 'c'; };

a.echo(); // 'ac'

b.__proto__.echo = ClassA.prototype.echo;

b.echo(); // 'bc'

ClassA.prototype.echo === ClassB.prototype.echo; // true
