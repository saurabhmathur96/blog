---
layout: post
title:  "Safer input in C"
date:   2015-09-10 20:24:00
categories: jekyll
---

# Why not to use scanf
`scanf` is the standard method to get structured, formatted input in C.  
The problems with `scanf` are:

+ While it is extremely powerful, it is not very robust when it comes to error recovery. It does tell you if it has succeeded or failed (through the return value) but basically, that's all.
+ Reading strings with `%s` has the same vulnerability as `gets` - it does not check the size of your string, which may be longer than the input causing overflow.
+ It does not ignore whitespace. This means, that newlines are treated as characters. This is a problem when you are reading single `chars`. If the user enters a single `char` and presses enter, a newline character (`'\n'`) is also added to the buffer. Now when you try to read another`char`, the `'\n'` is read.


 [A more detailed explaination is on c-faq.com](http://c-faq.com/stdio/scanfprobs.html).

# An alternative
 A quick search on [stackoverflow](http://stackoverflow.com/questions/9278226/which-is-the-best-way-to-get-input-from-user-in-c) showed that using `fgets` to read strings is considered a good option.  
 To read `ints` and `floats` the `sscanf` function can be used. `sscanf` is a function used to take formatted "input" from strings.  

 `fgets` has another quirk - it reads the `'\n'` into the string too. This can be resolved by checking the last character.
 Here's how I implemented a `read_line` function that reads strings of given size thus avoiding overflow.

 {% highlight c %}
int read_line(char *line, int size)
{
    fgets(line, size, stdin);

    int length = strlen(line);

    if(line[length-1] == '\n')
    {
        line[length-1] = '\0';
        length--;
    }

    return length;
}
 {% endhighlight %}

 This function can be used to implement a `read_int` function that asks the user to re-enter the input if the input is invalid.

 {% highlight c %}
int read_int()
{
    char line[256];
    read_line(line, sizeof line);
    int i;
    if(sscanf(line, "%d", &i) == 1)
    {
        return i;
    }
    else
    {
        printf("\"%s\" is not an integer. Retry: ", line);
        return read_int();
    }
}
{% endhighlight %}
