
I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.

I created this change independent from any other sources.

# Mystery Function

What does the `mystery()` function in the following piece of code do? Add your
answer to this markdown file.

```javascript
function mystery(a) {
    if(a.length == 1) return a[0];
    var foo = mystery(a.slice(1, a.length))
    if(foo > a[0]) return foo;
    else return a[0];
}
```

Analyzing each component of this JavaScript function:
This line returns the first (and only) element of a in the case where a has only one element:
if(a.length == 1) return a[0];

Now to examine:
var foo = mystery(a.slice(1, a.length));
Breaking it up:

This part gets all the elements of a, excluding the very first one:
a.slice(1, a.length);

So, we can see:
var foo = mystery(a.slice(1, a.length));
is a recursive call where foo is set to the result of mystery called on all elements of a except the first one. foo then holds the maximum value found in this sub-array and is passed back into the function.

This part will return foo if foo is greater than the first element of a, or else it will return the first element of a:
if(foo > a[0]) return foo;
else return a[0];

In a paragraph, the function will recursively use foo to call the mystery function with shorter and shorter sub-arrays, removing the first element of the array in each iteration until it is called with a single value, which will then be returned, and the recurssion will begin to work backwards. As the iterations progress, it will keep comparing two values: the a[0] of the relevant sub-array and foo. It will return the larger value to use as foo in the next comparison. This continues until the function returns the largest value in the array.
