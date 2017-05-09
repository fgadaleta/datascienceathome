---
layout: post
title: Getting ready for Big Data analytics and optimization in Python
tags: [analytics, big-data, coding, computer-science, optimization, programming, python]
---
The increasing popularity of Python as a language for Big Data analysis is yet
another reason to learn some optimization techniques to write software that
can scale easily without putting the hardware infrastructure under stress (for
nothing). Here is a list of optimization strategies, from string manipulation
to loops. The list is _non-exhaustive,_ but a great starting point to improve
your code.

### No string pumping in a for loop

Whenever you are dealing with large strings, avoid pumping the string in a
_for_ loop, which is usually done by this:

    
    
    s = ""
    for substr in list:
        s += substr

Instead you should use `s = "".join(list)`.  The same applies when you are
generating strings via a function foo:

    
    
    s = ""
    for x in list:
        s += foo(x)

This is much better:

    
    
    slist = [foo(x) for x in somelist]
    s = "".join(slist)

Still in the realm of string manipulation, pumping a string with

    
    
    out = "<html>" + head + post + query + tail + "</html>"

is not nice, though correct. Instead, use the _sprintf_ C-like form

    
    
    out = "<html>%s%s%s%s</html>" % (head, post, query, tail)
    
    
    

### Appending the result of a function

Other scenario: you want to append to a list the result of a function. An
optimization that will save you **a lot** of time is reported in the snippet
below. Let's say that you are converting to uppercase the words of a list. A
naive programmer would write

    
    
    newlist = []
    for word in oldlist:
        newlist.append(word.upper())

That's correct. But terribly slow. The _for_ loop, the string manipulation
function and the append function will crash a pretty powerful computer
whenever crunching on very large lists. The function _map_ will get rid of the
interpreted loop and switch to the _C-compiled loop_, of the Python virtual
machine.

Check it out

    
    
    newlist = map(str.upper, oldlist)
    
    

### Use local variables

Another trick that most programmers ignore is about using local variables. The
lookup system of the Python interpreter is much more efficient with local than
global variables. Moreover the code will be much more readable.

Write something like this

    
    
    def foo():  
      upper = str.upper  
      newlist = []  
      append = newlist.append  
    
    for word in oldlist:  
      append(upper(word)) 
     
    return newlist

### Fast histogram without plotting

This one might seem a bit off topic. But since that's quite common in data
analysis I will report it here. A recent improvement I found allowed me to
compute the histogram of a dataset without plotting it (which already saves a
lot of time) and is also much faster than the equivalent _matplot/pyplot_
version. The magic is in _numpy_. I was used to write this:

    
    
    from matplotlib import pyplot as plt
    binned_data = plt.hist(data, bins)[0]
    
    

Now I do this:

    
    
    import numpy as np 
    binned_data, bin_edges = np.histogram(data, bins)

Enjoy Python. Happy optimization!

