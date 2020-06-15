---
title: Var, let and const
date: "2020-03-22T22:12:03.284Z"
description: "The three methods of variable declaration in JavaScript"
---

In this article we'll discuss the three ways to create variables in JavaScript as well as the differences between
them and touch on some background topics needed to understand them.

## Var

Variables declared using `var` are either globally scoped or function scoped. Scope determines where variables and functions are accessible in your program. If a variables is declared with `var` outside of a function block in the below example then it is available to the whole window. However when declared inside a function block with `var`
then the variable can only be accessed within that function. Let's look at an example.

    var foo = "foo";

    function exampleFunction() {
        var bar = "bar";
    }

In this example the variable `foo` is globally scoped and the variable `bar` is function scoped. So we wouldn't be able to access the `bar` variable outside of the function.

The function scoping of `var` paired with the ability to redeclare a variable using the same identifier can cause major issues in your code as in this example.

    var foo = "foo";

    if(1 < 3) {
        var foo = "bar";
    }

    console.log(foo);

When we run this code you may be surprised to learn that the output in the console would actually be "bar" because the variable within the conditional statement replaces the original delcaration.

Hoisting in JavaScript is when variables and function declarations are moved to to the top of their scope before
code execution. So for example:

    console.log(foo);
    var foo = "foo";

Before execution this will be converted to the following:

    var foo;
    console.log(foo);
    foo = "foo";

This means that when we try to output the value of `foo` to the console the variable hasn't been initialized with a value yet and will instead show `undefined`.

## Let

The introduction of `let` replaced `var` as the preferred variable declaration method. It improves upon and solves some of the problems we've seen with `var`. Before touching on the differences it's worth explaining that in JavaScript a block is defined as anything between two curly braces i.e `{}`. A variable declared with `let` is blocked scoped meaning that it won't be available outside of the block it's declared within. Let's look at another example.

    var foo = "foo";

    function exampleFunction() {
        if(1 < 3) {
            var bar = "bar";
            let qux = "test";
        }

        console.log(bar);
        console.log(qux);

    }

This example builds off our previous example and can illustrate the scope difference between `let` & `var`. Due to `var` being function scoped we can successfully print to console the value of `bar` however due to the block scoped nature of `let` the variable we declared as `qux` won't be accessible because it's scoped is restricted to the block created by the if statement.

Hoisting with `let` works differently as well. Instead of being initialized as undefined, variables are instead not initialized at all. Trying to access these variables will result in a `ReferenceError`.

## Const

`const` plays a slightly different role to the other variable declaration methods. Variables declared using `const` are block scoped much like those declared using `let` however they cannot be updated. So we wouldn't be able to do the following.

    const myConst = "foo";
    myConst = "bar";

Hoisting in `const` behaves exactly the same as with `let`, declarations are hoisted to the top but not initialized.

## Conclusion

So now you've got to grips with the three different methods of variable declaration in JavaScript the natural question is well which one should I use? When declaring variables it is good practice to avoid using `var`, keeping our code in the right scope makes it a lot easier to manage. You can decide between when to use `let` or `const` by using the following rules:

1. Use `const` when you are sure that the variable won't change.
2. Use `let` when you will be changing the value of the variable.
