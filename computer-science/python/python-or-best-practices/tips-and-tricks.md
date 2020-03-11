---
description: '30 Python Best Practices, Tips, And Tricks'
---

# Tips And Tricks

Here are 30 Python best practices, tips, and tricks. I’m sure they’ll help you procrastinate your actual work, and still learn something useful in the process.

## 1. Use Python 3 <a id="8d12"></a>

In case you missed it: **Python 2 is** [**officially not supported as of January 1, 2020**](https://www.python.org/dev/peps/pep-0373/)**.** This guide has a bunch of examples that only work in Python 3. If you’re still on Python 2.7, upgrade _now_.

If you’re on MacOS, you can use [Homebrew to painlessly upgrade Python](https://medium.com/tech-explained/how-to-get-and-use-the-ultimate-macos-package-manager-f2ba5c9466d4).

## 2. Check for a minimum required Python version <a id="c72e"></a>

You can check for the Python version in your code, to make sure your users are not running your script with an incompatible version. Use this simple check:

## 3. Use IPython <a id="fa51"></a>

![](https://miro.medium.com/max/60/1*5zJJ4kGgnyk10Dx_t9R1qQ.png?q=20)![](https://miro.medium.com/max/1496/1*5zJJ4kGgnyk10Dx_t9R1qQ.png)Screenshot by author

[IPython](https://ipython.org/) is basically an enhanced shell. It’s worth it just for the autocompletion alone, but there is much more. I like it too for all the magic commands that are built-in. Here are a few :

* `%cd` — to change the current working directory
* `%edit` — to open an editor and execute the code you typed in after closing the editor
* `%env` — to show the current environment variables
* `%pip install [pkgs]` — to install packages without leaving the interactive shell
* `%time` and `%timeit` — to time the execution of Python code

Read the full list [here](https://ipython.readthedocs.io/en/stable/interactive/magics.html).

Another useful feature is referencing the output of a previous command. **In** and **Out** are actual objects. You can use the output of the 3rd command by using `Out[3]`.

Install IPython with:

`pip3 install ipython`

## 4. List Comprehensions <a id="eeca"></a>

A list comprehension can replace ugly for loops used to fill a list. The basic syntax for a list comprehension is:

```text
[ expression for item in list if conditional ]
```

A very basic example to fill a list with a sequence of numbers:

And because you can use an expression, you can also do some math:

Or even call an external function:

And finally, you can use the ‘if’ to filter the list. In this case, we only keep the values that are dividable by 2:

## 5. Check memory usage of your objects <a id="d9d8"></a>

With sys.getsizeof\(\) you can check the memory usage of an object:

Woah… wait… why is this huge list only 48 bytes?

It’s because the range function returns a _**class**_ that _****_only behaves like a list. A range is a lot more memory efficient than using an actual list of numbers.

You can see for yourself by using a list comprehension to create an actual list of numbers from the same range:

## 6. Return multiple values <a id="0d75"></a>

Functions in Python can return more than one variable without the need for a dictionary, a list or a class. It works like this:

This is alright for a limited number of return values. But anything past 3 values should be put into a \(data\) class.

## 7. Use data classes <a id="f794"></a>

Since version 3.7, Python offers data classes. There are several advantages over regular classes or other alternatives like returning multiple values or dictionaries:

* a data class requires a minimal amount of code
* you can compare data classes because `__eq__` is implemented for you
* you can easily print a data class for debugging because `__repr__` is implemented as well
* data classes require type hints, reduced the chances of bugs

Here’s an example of a data class at work:

An in-depth guide can be found [here](https://realpython.com/python-data-classes/).

## 8. In place variable swapping <a id="a066"></a>

A neat little trick that can save a few lines of code:

## 9. Merging dictionaries \(_Python 3.5+\)_ <a id="ab05"></a>

Since Python 3.5, it became easier to merge dictionaries:

If there are overlapping keys, the keys from the first dictionary will be overwritten.

## 10. String to title case <a id="5c72"></a>

This is just one of those lovely gems:

## 11. Split a string into a list <a id="f428"></a>

You can split a string into a list of strings. In this case, we split on the _space_character:

To split on whitespace, you actually don’t have to give split any arguments. By default, all runs of consecutive whitespace are regarded as a single whitespace separator by `split`. So we could just as well use `mystring.split()`.

## 12. Create a string from a list of strings <a id="6e75"></a>

And vice versa from the previous trick, create a string from a list and put a space character between each word:

If you were wondering why it’s not `mylist.join(" ")` — good question!

It comes down to the fact that the String.join\(\) function can join not just lists, but any iterable. Putting it inside String prevents implementing the same functionality in multiple places.

## 13. Emoji <a id="621e"></a>

![](https://miro.medium.com/max/60/1*5wWvIDF3MAJdPYEUI3InuA.png?q=20)![](https://miro.medium.com/max/1280/1*5wWvIDF3MAJdPYEUI3InuA.png)Image by [Pixaline](https://pixabay.com/nl/users/Pixaline-1569622/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2762568) on [Pixabay](https://pixabay.com/nl/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2762568)

This one will either impress or repulse, depending on who’s looking. On a more serious note, this can come in handy _especially when analyzing social media data_.

First, install the emoji module:

```text
pip3 install emoji
```

With this installed, you can do as follows:

Visit the [emoji package page](https://pypi.org/project/emoji/) for more examples and documentation.

## 14. Slicing a list <a id="fd6e"></a>

The basic syntax of list slicing is:

```text
a[start:stop:step]
```

`Start`, `stop` and `step` are optional. If you don’t fill them in, they will default to:

* 0 for `start`
* the end of the string for `end`
* 1 for `step`

Here are some examples:

## 15. Reversing strings and lists <a id="fb42"></a>

You can use the slice notation from above to reverse a string or list. By using a negative stepping value of -1, the elements are reversed:

## 16. Display kittens <a id="1f7c"></a>

I finally found a good excuse to include kittens in one of my articles! You, however, might use it to display graphs and such. First, install [Pillow](https://pypi.org/project/Pillow/), a fork of the Python Image Library:

```text
pip3 install Pillow
```

Now download this image to a file called kittens.jpg:![](https://miro.medium.com/max/60/1*lUDXx0e6yLs5F--u-b4A0Q.jpeg?q=20)![](https://miro.medium.com/max/1920/1*lUDXx0e6yLs5F--u-b4A0Q.jpeg)Image by [TheDigitalArtist](https://pixabay.com/nl/users/thedigitalartist-202249/) on [Pixabay](https://pixabay.com/nl/photos/kittens-katten-huisdier-cute-2641211/)

You can use the following code to display the image from your Python code:

Or you can do it right from IPython:![](https://miro.medium.com/freeze/max/60/1*D8q1kVPE9SDdnWqOQpAMyg.gif?q=20)![](https://miro.medium.com/max/640/1*D8q1kVPE9SDdnWqOQpAMyg.gif)It’s me, looking at kittens

Pillow can do a lot more than displaying the image. It can analyze, resize, filter, enhance, morph, etcetera. See the [documentation](https://pillow.readthedocs.io/en/stable/) for all its features.

## 17. Using map\(\) <a id="c70d"></a>

One of Python’s built-in functions is called `map()`. The syntax for `map()` is:

`map(function, something_iterable)`

So you give it a function to execute, and something to execute on. This can be anything that’s iterable. In the examples below I’ll use a list.

Take a look at your own code and see if you can use `map()` instead of a loop somewhere!

## 18. Get unique elements from a list or string <a id="93f2"></a>

By creating a set with the `set()` function, you get all the unique elements from a list or list-like object:

## **19. Find the most frequently occurring value** <a id="3a68"></a>

To find the most frequently occurring value in a list or string:

Do you understand why this works? Try to figure it out for yourself before reading on.

You didn’t try, did you? I’ll tell you anyway:

* `max()` will return the highest value in a list. The `key` argument takes a single argument function to customize the sort order, in this case, it’s test.count. _The function is applied to each item on the iterable._
* `test.count` is a built-in function of list. It takes an argument and will count the number of occurrences for that argument. So `test.count(1)`will return 2 and `test.count(4)` returns 4.
* `set(test)` returns all the unique values from test, so {1, 2, 3, 4}

So what we do in this single line of code is take all the unique values of test, which is `{1, 2, 3, 4}`. Next, `max` will apply the `list.count` function to them and return the maximum value.

And no — I didn’t invent this one-liner.

## 20. Create a progress bar <a id="06ec"></a>

You can create your own progress bar, which is fun to do. But it’s quicker to use the _progress_ package:

`pip3 install progress`

Now you can create a progress bar with minimal effort:

The following animation demonstrates all the available progress types:![](https://miro.medium.com/freeze/max/60/1*JAQfXWEmuu-9Cvvd5LZPpg.gif?q=20)![](https://miro.medium.com/max/640/1*JAQfXWEmuu-9Cvvd5LZPpg.gif)Animation by Giorgos Verigakis from [progress](https://pypi.org/project/progress/)

## 21. Use the \_ in an interactive shell <a id="b91b"></a>

You can obtain the result of the last expression with the underscore operator, e.g. in IPython this looks like:

```text
In [1]: 3 * 3
Out[1]: 9In [2]: _ + 3
Out[2]: 12
```

This works in the Python shell too. In addition, the IPython shell allows you to use `Out[n]` to get the value of the expression `In[n]`. E.g., `Out[1]` would give us the number 9 in the example above.

## 22. Quickly create a web server <a id="b984"></a>

You can quickly start a web server, serving the contents of the current directory:

```text
python3 -m http.server
```

This is useful if you want to share some stuff with a co-worker or want to test a simple HTML site.

## 23. Multi-Line Strings <a id="6b22"></a>

Although you can use triple quotes to include multi-line strings in your code, it’s not ideal. Everything you put between the triple quotes becomes the string, including the formatting, as you can see below.

I prefer the second way, which concatenates multiple lines together, allowing you to format your code nicely. The only downside is that you need to explicitly put in newlines.

## 24. Ternary Operator For Conditional Assignment <a id="69b3"></a>

This is another one of those ways to make your code more concise while still keeping it readable:

```text
[on_true] if [expression] else [on_false]
```

As an example:

```text
x = "Success!" if (y == 2) else "Failed!"
```

## 25. Counting occurrences <a id="32e9"></a>

You can use Counter from the collections library to get a dictionary with counts of all the unique elements in a list:

## 26. Chaining of comparison operators <a id="ed65"></a>

You can chain comparison operators in Python, creating more readable and concise code:

## 27. Add some color <a id="2a27"></a>

![](https://miro.medium.com/max/60/1*nc8J3Tff07gsYsvguqT-Fg.png?q=20)![](https://miro.medium.com/max/661/1*nc8J3Tff07gsYsvguqT-Fg.png)Screenshot by Jonathan Hartley from [Colorama](https://pypi.org/project/colorama/)

With [Colorama](https://pypi.org/project/colorama/), you can add some color to your terminal.

## 28. Working with dates <a id="8c55"></a>

The p[ython-dateutil](https://pypi.org/project/python-dateutil/) module provides powerful extensions to the standard datetime module. Install it with:

```text
pip3 install python-dateutil 
```

You can do so much cool stuff with this library. I’ll limit the examples to just this one that I found particularly useful: fuzzy parsing of dates from log files and such.

Just remember: where the regular Python datetime functionality ends, python-dateutil comes in!

## 29. Integer division <a id="914d"></a>

![](https://miro.medium.com/max/60/1*wB-kSi6AhKUuUTcI_KwGbw.jpeg?q=20)![](https://miro.medium.com/max/800/1*wB-kSi6AhKUuUTcI_KwGbw.jpeg)By [Torindkflt](https://commons.wikimedia.org/w/index.php?curid=11109755) — Public Domain

In Python 2, the division operator \( / \) defaults to an integer division, unless one of the operands is a floating-point number. So you have this behavior:

```text
# Python 2
5 / 2 = 2
5 / 2.0 = 2.5
```

In Python 3, the division operator defaults to a floating-point division and the // operator has become an integer division. So we get:

```text
Python 3
5 / 2 = 2.5
5 // 2 = 2
```

For the complete motivation behind this change, you should read [PEP-0238](https://www.python.org/dev/peps/pep-0238/).

## 30. Charset detection with chardet <a id="ce3c"></a>

You can use the chardet module to detect the charset of a file. This can come in very useful when analyzing big piles of random text. Install with:

`pip install chardet`

You now have an extra command-line tool called chardetect, which can be used like this:

```text
chardetect somefile.txt
somefile.txt: ascii with confidence 1.0
```

You can also use the library programmatically, [check out the docs](https://chardet.readthedocs.io/en/latest/usage.html).

