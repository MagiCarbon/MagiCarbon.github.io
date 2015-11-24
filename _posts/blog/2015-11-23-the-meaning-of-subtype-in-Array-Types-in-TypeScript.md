---
layout: post
categories: blog
share: true
comments: true
title: the meaning of 'subtype' in Array Types in TypeScript
excerpt: there's something called 'subtype' which is sooo hard to understand in the part of "Array Types" in the official handbook
date: '2015-11-23T18:00:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [TypeScript]
author: MC
hidelogo: true
---

dear me,
recently, learning TypeScript by reading the official handbook. sometimes i feel myself so stupid.

i dunno, just cant figure out the meaning of 'subtype';

### here is some example of 'subtype'.

>There are two types of supported index types: string and number. It is possible to support both types of index, with the restriction that the type returned from the numeric index must be a subtype of the type returned from the string index.
> - [Official HandBook](http://www.typescriptlang.org/Handbook#interfaces-array-types){:target="_blank"}

```typescript
interface StringNumberArray {
    [index: string]: string;
    [index: number]: string; //numbric index must be a type of 'string' as same as the type of string index
}
```

*or*

```typescript
//i think this case is better, which is more 'subtype-style'.
interface StringNumberArray {
    [index: string]: {a:string};
    [index: number]: { a: string, b: string };
}
```

>While index signatures are a powerful way to describe the array and 'dictionary' pattern, they also enforce that all properties match their return type. In this example, the property does not match the more general index, and the type-checker gives an error:
> - [Official HandBook](http://www.typescriptlang.org/Handbook#interfaces-array-types){:target="_blank"}

```typescript
interface Dictionary {
  [index: string]: string;
  length: number;    // error, the type of 'length' is not a subtype of the indexer
}
```

in above case, the type of property 'length' must be a 'string'!!

```typescript
interface Dictionary {
  [index: string]: {a: string};
  length: {a: string}; // here must be '{a: string}' type
}
```
