---
layout: post
title: Think twice before using varargs
---

Varargs, which is short for
[variadic arguments](https://en.wikipedia.org/wiki/Variadic_function),
are a pretty cool thing. They allow your functions to take from 0 to n
arguments, the amount of possible function arguments might differ from
language to language though. Most of you have probably already used a
function which makes use of varargs. Throughout this blog post, I am gonna
use Java for examples.

As an example, let's look at [String.format(String, Object...)](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#format(java.lang.String,%20java.lang.Object...)):

```Java
String name = "Marcel"
String.format("Hello %s.%nThe weather is quite good today.", name);
```

The resulting String would look like this:

```plaintext
Hello Marcel.
The weather is quite good today.
```

We could also use the function to just add a line break, but pass no additional
variables:

```Java
String name = "Marcel"
String.format("Hello.%nThe weather is quite good today.");
```

This would still compile, since varargs allow from 0 to n arguments, which
is totally fine for our use case though.

But let's look at a more dangerous example:

```Java
class Screamer {
    /**
     * Screams each passed word onto a new line.
     *
     * @params words are the things to be screamed
     */
    void screamWords(String... words) {
        for( String word: words ) {
            System.out.println("Scream: " + words.toUpperCase());
        }
    }
}

class IntenseScreamer extends Screamer{
    @Override
    void screamWords(String... words) {
        //Intensify the words by adding exclamation marks!
        for( int index = 0; index < words.length; index++ ) {
            words[index] = words[index] + "!!!";
        }

        super.screamWords();
    }
}
```

In case you haven't noticed the error, I forgot passing the words to the
supercall. That happens quite easy, since it allows 0 arguments as well.
In such case, an empty array will be passed, since varargs are nothing but
arrays under the hood.

I am not telling you to avoid varargs completely, but sometimes you might just
want to use an array, as it will give you some compile-time safety, since you
have to at least pass an empty array.

In my opinion, you should avoid using varargs if you could potentially pass
an incorrect amount of values, since there can not be any compile-time checking
without using third party tools.

This actually happened to me at work, which is why I bring it up. I wasted a
while before I found the problem, since I didn't check every place where the
parameters were passed on. I just knew that nobody mutates them and I knew
that they were passed correctly in the beginning, so why the hell was I
getting an empty array.

**EDIT:**

A colleague pointed out that it might annoy some people to always create arrays,
which is kind of the reason why varargs are so nice to use. A possible solution
to that problem would be a mandatory parameter followed by a vararg parameter of
the same type.

Here is an example:

```Java
//Defining your method
void hello(String nameOne, String... restOfNames) {
    String names[] = new String[restOfNames.length + 1];
    names[0] = nameOne;
    System.arraycopy(restOfNames, 0, names, 1, restOfNames.length);

    //Implementation...
}

//Calling it
hello("Marcel", "Jeff", "John");
```

As you can see, this requires some additional logic, but it would usage wise be
the same for the methodcaller, unless the intention was to actually pass a
complete array, in that case the caller would have to create a new smaller array
and pass the first cell of the old array as the first parameter. This would also
be worse performance wise, even though this would usually not be critical.