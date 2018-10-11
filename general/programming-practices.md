# 💻 General Programming Practices

As we work with a high number of languages at native levels, we tend to pick up on general programming practices and 
principles that we believe are consistent between them.

This page looks to concisely sum most of them up. The examples in this page are using PHP, as to target the majority
of our programming internally, but the principles should apply across languages, meaning variable/method casing could 
change, dependant on that languages standards.

#### Self Documentation

Code should be [Self Documenting](https://en.wikipedia.org/wiki/Self-documenting_code), to the level that people should 
be able to read it without much hassle.

You may find that sometimes functions/methods can be highly mathematical or complex, in which case it can still be hard 
to follow, even with good variable and function names. This is when comments should be appropriately used to document 
code.

You should AVOID obvious comments.

#### Variables

Following on from [Self Documenting Code](https://en.wikipedia.org/wiki/Self-documenting_code), Variable names should be 
descriptive.

Instead of abbreviating `$quoteOrder` to `$qO`, keep it longer as to make the code more obvious.

#### Methods / Functions

Following on from [Self Documenting Code](https://en.wikipedia.org/wiki/Self-documenting_code), Method / Function names
should be descriptive.

Instead of abbreviating `createInvoiceInXero()` to `invoice()`, keep it longer as to make the functions intention more 
obvious.

#### Indentation

Indentation should be consistent throughout a project. If the language's standards dictate that 4 space should be used,
then EVERY file in that project should have a consistent 4 spaces per indent, instead of a mismatch of 2 and 4.

#### Line Length

Line length can differ based upon language, but should be kept to the standard. This means that developers can;
- Keep their window the same size
- Not have singular lines be difficult to read/have multiple purposes

You can adhere to this by ensuring you aren't chaining methods.

#### Don't Repeat Yourself (DRY) Principle

In order to keep maintenance costs down, we should try to not have code repeated throughout a system, as a change to 
this code would end up in having to repeat the change in all occurrances, when most of the time common code can be 
abstracted out and reused.

#### Structure

As projects grow, more and more files get added to them. Just like a file system on your computer, if you don't implement
a solid folder structure and give everything a house then files can become hard to find, and other developers will find
it difficult to pick up the project. 