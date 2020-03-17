# Dynamic Programming: From Zero to Hero

Dynamic programming has an intimidating reputation, but when you get down to it the concepts are actually fairly simple.

In this post I’ll attempt to expose the simplicity of dynamic programming and diminish its intimidating reputation. I’ll do this by optimizing the classic algorithm problem: Find the nth number in the fibonacci sequence. I’ll start off with a bad solution and work my way to the most optimal.

### Solution Overview: <a id="ad07"></a>

1. Basic Recursive Implementation \(Time: O\(2ⁿ\), Space: O\(n\)\)
2. Recursive Implementation with Memoization \(Time: O\(n\), Space: O\(n\)\)
3. Bottom Up Iterative Implementation with Caching \(Time: O\(n\), Space: O\(n\)\)
4. Bottom up Iterative Implementation \(Time: O\(n\), Space: O\(1\)\)

![](https://miro.medium.com/max/60/1*CHNw4tU5iYVQt0zco1qXyQ.png?q=20)![](https://miro.medium.com/max/1844/1*CHNw4tU5iYVQt0zco1qXyQ.png)This is you, doing dynamic programming in your sleep after reading this blog post.

## The Fibonacci Sequence <a id="c690"></a>

The fibonacci sequence is a sequence of numbers starting from 0 and 1, where each number is the sum of the two preceding numbers. For example, the next \(3rd\) number in the sequence will be 1, because 0 + 1 = 1, and so on. The example below might make this more clear.

The first 8 fibonacci numbers are:

```text
0, 1, 1, 2, 3, 5, 8, 13, ...
```

This can be described mathematically like so:![](https://miro.medium.com/max/60/1*IijhBTnwAEPTQ3ZP7L70vA.png?q=20)![](https://miro.medium.com/max/304/1*IijhBTnwAEPTQ3ZP7L70vA.png)

_where_![](https://miro.medium.com/max/60/1*OouWXtGIbl65_JflaKH90w.png?q=20)![](https://miro.medium.com/max/304/1*OouWXtGIbl65_JflaKH90w.png)

_and n &gt; 1_

## The Problem <a id="a6ba"></a>

Find the nth value in the Fibonacci sequence. In other words, given _n_ find _fn_where _fn_ is the _nth_ value in the fibonacci sequence.

For example, if we reference our fibonacci sequence above, if our input is 8 our output should be 13. Pretty straightforward.

## **Basic Recursive Implementation** <a id="b3f0"></a>

> Time Complexity: O\(2_ⁿ_\)
>
> Space Complexity: O\(n\)

The first and easiest implementation is a recursive function modeled off of the fibonacci definition _Fn = Fn-1 + Fn-2_, where the starting values _F₀ = 0_, _F₁ = 1_ serve as our break out case:**Basic Recursive Implementation**

As you can see this implementation is beautifully derived from the mathematical fibonacci definition. However, it may not be an optimal solution. Let’s investigate the recursive call stack to determine our time and space complexity.

Let’s use _n = 5_ as an example to think about what this implementation is doing. Initially the function is called, fibonacci\(5\). fibonacci\(5\) will then recursively call fibonacci\(4\) and fibonacci\(3\). fibonacci\(4\) will then call fibonacci\(3\) and fibonacci\(2\). And so on until we hit our break out cases of fibonacci\(1\) and fibonacci\(0\).![](https://miro.medium.com/max/60/1*5TiToopxWeHXCiSzfhdNWw.png?q=20)![](https://miro.medium.com/max/2376/1*5TiToopxWeHXCiSzfhdNWw.png)**The Recursive Call Tree when n = 5. Each node denotes a call to fibonacci\(n\).**

As you can see, the number of function calls double for every new level in the call tree. This is because our _fibonacci_ function calls itself twice. Therefore, the time complexity of this implementation is _O\(2ⁿ\)_\[1\]. For every new level _n_ the number of operations double.\[2\] This is not an optimal run time as you can see:![](https://miro.medium.com/max/60/1*5kIxfN2goP8qfFWjZmUvMQ.jpeg?q=20)![](https://miro.medium.com/max/1464/1*5kIxfN2goP8qfFWjZmUvMQ.jpeg)**O\(2ⁿ\) is “Horrible”**

What about the space complexity?

Again, let’s dig into how this function actually works. This function will recursively call the first instance of itself every time until it hits a break out case. Here’s a visualization of what the call **stack** actually looks like when we hit that first break out case:![](https://miro.medium.com/max/60/1*-5t_PJUX7uwslE3suFbrOQ.png?q=20)![](https://miro.medium.com/max/1132/1*-5t_PJUX7uwslE3suFbrOQ.png)The recursive call **stack** when _n = 5_ and we hit our **first** break out case. Note that the recursive call stack is different from a tree in that the tree displays every function that will be called, whereas the stack displays a snapshot of the tree at a single point in time.![](https://miro.medium.com/max/60/1*IAs0YNrcyyqd4Fa0JBR-BQ.png?q=20)![](https://miro.medium.com/max/1162/1*IAs0YNrcyyqd4Fa0JBR-BQ.png)The recursive call **stack** when n = 5 and we hit our **second** break out case. Note: call stack is 5 methods deep at this point, therefore the max space consumed when n = 5 is 5. i.e. given n, space complexity is O\(n\).

In other words the recursive call **stack** only traverses one branch of the recursive call **tree** at a time. Therefore, the space complexity of this implementation is _O\(n\)_ where _n_ is the depth of the recursive call tree. This is apparent in our above examples where _n = 5_ and the call stack is _5_functions deep.

### Basic Recursive Implementation Conclusion <a id="dba2"></a>

Time: O\(2ⁿ\)

* Really bad, let’s fix this first.

Space: O\(n\)

* Not terrible, but can we make it better later down the line?

## Recursive Implementation with Memoization <a id="1f3b"></a>

> Time Complexity: O\(n\)
>
> Space Complexity: O\(n\)

If we reexamine the recursive call tree from the example above we can see that we’re repeating function calls. I’ve highlighted the repeated calls in the below tree:![](https://miro.medium.com/max/60/1*AS9DlOlYe7clTyrjan_P3Q.png?q=20)![](https://miro.medium.com/max/1412/1*AS9DlOlYe7clTyrjan_P3Q.png)The recursive call **tree** when n = 5 with highlighted duplicate function calls

Woah, we’re calling _f\(3\)_ twice, _f\(2\)_ a few times, etc.. Every time we call those it triggers an entire new call tree from that node. i.e, every time we call f\(3\) it triggers this call tree:![](https://miro.medium.com/max/60/1*0HRvSsW_45SYJi1ekHV17g.png?q=20)![](https://miro.medium.com/max/744/1*0HRvSsW_45SYJi1ekHV17g.png)

That’s extremely inefficient. We can reduce this duplicate work by storing the value of the first call to _f\(3\)_, then using that value for any future calls instead of recalculating it.

Let’s explore what our call tree looks like after preventing duplicate function calls:![](https://miro.medium.com/max/60/1*ANyzvbzfQozv-90zIFO-yg.png?q=20)![](https://miro.medium.com/max/1150/1*ANyzvbzfQozv-90zIFO-yg.png)Call **tree** when n = 5 with memoization \(duplicate function calls prevented\)![](https://miro.medium.com/max/60/1*xLn7z5Tpx6Dy7Rj0CTYvMg.png?q=20)![](https://miro.medium.com/max/998/1*xLn7z5Tpx6Dy7Rj0CTYvMg.png)This is what the call **stack** looks like when we store our first value

In the above image, we’ve traversed down the call stack, hit our break out cases, and we’ve bubbled back up the call stack and have the solution for _f\(2\)_. Here we’ll store _f\(2\)_. i.e. our cache will look like _{ 2: 1 }_. The next time we want to calculate _f\(2\)_ we can just reference our cache.![](https://miro.medium.com/max/60/1*ceFVaaPu5gQTkhWuu019Vw.png?q=20)![](https://miro.medium.com/max/1070/1*ceFVaaPu5gQTkhWuu019Vw.png)The next time our call **stack** hits f\(2\) we’ve already calculated and stored f\(2\) so we can reference our cache instead of going down the f\(2\) call tree.

When we cache values we only have to traverse down the left side of the call tree. When historically we would traverse to the right we can use our stored values, and we don’t have to traverse to the right. i.e. we only have to traverse down and back up n nodes. Therefore our time complexity becomes O\(n\). This is even more apparent if we have another look at our updated call **tree**:![](https://miro.medium.com/max/60/1*ANyzvbzfQozv-90zIFO-yg.png?q=20)![](https://miro.medium.com/max/1150/1*ANyzvbzfQozv-90zIFO-yg.png)Call **tree** when n = 5 with memoization \(duplicate function calls removed\)

Our space complexity in this implementation is the same. _O\(n\)_. We still need to recurse down _n_ levels as we can see from the call tree. We are also storing _n_ items in a map. _O\(2n\)_ simplifies to _O\(n\)_.

### Recursive Implementation with Memoization Conclusion <a id="08a8"></a>

Time: O\(n\)

* Way better than _O\(2ⁿ\)_. In fact, this is the best conceivable runtime for this algorithm because in order to calculate the _nth_ fibonacci number we’ll need at least _n_ operations. So we’re good on time, let’s investigate if we can improve memory.

Space: O\(n\)

* Again, not bad, but I think we can do better. Do we really need to store _n_values for this calculation? If you think about it, we only really need the previous two values to calculate the next value. With that in mind, we know it’s possible solve this in _O\(1\)_ space. Additionally, we know we can’t do it recursively because of the nature of the recursive call stack. A recursive solution would have to use at least _O\(n\)_ space. We have to go bottom up. Instead of going all the way to the _O\(1\)_ solution, let’s see if we can come up with a bottom up approach that utilizes what we already know.

## Bottom Up Iterative Implementation with Caching <a id="5f67"></a>

> Time: O\(n\)
>
> Space: O\(n\)

Let’s think one more time about what’s happening in our memoization solution.![](https://miro.medium.com/max/60/1*ANyzvbzfQozv-90zIFO-yg.png?q=20)![](https://miro.medium.com/max/1150/1*ANyzvbzfQozv-90zIFO-yg.png)Memoization call tree pasted again for reference

If we think about it, all of the real calculations are occurring as we bubble back up the left side of our call stack. We hit our break out cases _f\(1\)_ and _f\(0\)_ then use those values to calculate _f\(2\)_. Then we use _f\(2\)_ and our cached value of _f\(1\)_ to calculate _f\(3\)_. We use _f\(3\)_ and our cached _f\(2\)_ to calculate _f\(4\)_ and so on until we are in the initial function call and return the result.![](https://miro.medium.com/max/60/1*Ayxf4eT2P89LbgYlDwaYRA.png?q=20)![](https://miro.medium.com/max/1166/1*Ayxf4eT2P89LbgYlDwaYRA.png)Bubbling up out of the call stack in our recursive solution

Our bottom up approach can basically mimic the bubbling up behavior of our memoization approach. We just need to iterate up to n. As we iterate we calculate and cache values to use in the next calculation.

Beautiful.

### Bottom Up Iterative Implementation with Caching Conclusion: <a id="7b91"></a>

Time: O\(n\)

* Best conceivable runtime still, yay.

Space: O\(n\)

* Again not bad, but if we examine our solution we’ll notice that for each new fibonacci number we only need the two previous fibonacci numbers. Therefore, we can achieve constant space if we only keep track of the two previous values. Let’s do it.

## Bottom Up Iterative Implementation <a id="a58f"></a>

> Time: O\(n\)
>
> Space: O\(1\)

## Bottom Up Iterative Implementation Conclusion: <a id="06af"></a>

Time: O\(n\)

* Still best conceivable runtime, yay.

Space: O\(1\)

* Doesn’t get better than that! Nice work!

### Conclusion <a id="64fd"></a>

The optimal approach looks so simple and makes so much sense. I’m sure it’s the intuitive solution for many people. So why does dynamic programming have such a reputation about it? Well, I’m not exactly sure. However, in my case it’s reputation prevented me from diving into it earlier on in my self taught career. I can only assume this is also the case for a few other people out there. Hopefully this post helps diminish that undeserved reputation and more self taught coders feel confident diving into dynamic programming.

Thanks for reading,

Zach

\[1\] This can be a helpful pattern to remember. For any recursive function that follows this structure the runtime will be _O\(xⁿ\)_. Where x is the number of times the recursive function calls itself and n is the depth of the recursive call stack.

\[2\] You may notice that the levels don’t perfectly double every time. The 

