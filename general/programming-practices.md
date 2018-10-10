# 💻 General Programming Practices

As we work with a high number of languages at native levels, we tend to pick up on general programming practices and 
principles that we believe are consistent between them.

This page looks to concisely sum most of them up. The examples in this page are using PHP, as to target the majority
of our programming internally, but the principles should apply across languages, meaning variable/method casing could 
change, dependant on that languages standards.

#### General

Code should be [Self Documenting](https://en.wikipedia.org/wiki/Self-documenting_code), to the level that people should 
be able to read it without much hassle.

You may find that sometimes functions/methods can be highly mathmatical or complex, in which case it can still be hard 
to follow, even with good variable and function names. This is when comments should be appropriately used to document 
code.

#### Variables

Following on from [Self Documenting Code](https://en.wikipedia.org/wiki/Self-documenting_code), Variable names should be 
descriptive.

Instead of abbreviating `$quoteOrder` to `$qO`, keep it longer as to make the code more obvious.

#### Methods / Functions

Following on from [Self Documenting Code](https://en.wikipedia.org/wiki/Self-documenting_code), Method / Function names
should be descriptive.

Instead of abbreviating `createInvoiceInXero()` to `invoice()`, keep it longer as to make the functions intention more 
obvious.
