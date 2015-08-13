> The difference between `==` and `===` is usually characterized that `==` checks for value equality and `===` checks for both value and type
equality. However, this is inaccurate. The proper way to characterize
them is that `==` checks for value equality with coercion allowed, and
`===` checks for value equality without allowing coercion; `===` is often called "strict equality" for this reason.

https://github.com/getify/You-Dont-Know-JS/blob/master/up%20&%20going/ch2.md
