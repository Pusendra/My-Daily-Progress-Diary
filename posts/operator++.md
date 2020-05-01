---
title: 'How ++ operator works in javascript?'
tags: ["javascript"]
published: true
date: '2020-05-01'
---

Have you wondered how the javascript '++' operater works?

Let's see if you could answer these questions about javascript '++' operator.


```
let x = 30;

x++ // What is the value of x here? 

x   // what is the value of x here? 


++x // what is the value of x here?  

x   // what is the value of x here?  
```
<br>

Have you thought the answers of above question ?<br>
Lets check if your answer is true or false.

```
let x = 30;

x++ // What is the value of x here? 30

x   // what is the value of x here? 31


++x //?? 32

x   //?? 32
```
Does your answer matched with the above answer I have given? If not you need to understand how the javascript ++ operator works.

Until I watched kyle simpson course and read the javascript spec I thought ++x and x++ work as follows....


```
x = x+1;
```
<br>
Did you also thought that ++ operator works likes this ?

lets see what x = x+1; and y++ does for string.

```
let x = "6";
x = x+1 //?? "61"

let y = "6";
y++ // ?? 6
y //7
```
<br>

Did you see how ```x=x+1;``` and ```y++;``` works diffrently?

Have you read any part of the specification if not you can read here : https://www.ecma-international.org/ecma-262/10.0/index.html#sec-update-expressions

Lets see what does JS specification says about ++ operator.

```
12.4.6.1Runtime Semantics: Evaluation
UpdateExpression:++UnaryExpression
Let expr be the result of evaluating UnaryExpression.
Let oldValue be ? ToNumber(? GetValue(expr)).
Let newValue be the result of adding the value 1 to oldValue, using the same rules as for the + operator (see 12.8.5).
Perform ? PutValue(expr, newValue).
Return newValue.
```
Lets turn above algorithm into a function and see how x++ operator works>
```
function plusPlus(orginal_val){
let orginal_coerced_val = Number(orginal_val);
orginal_val = orginal_coerced_val + 1;
return orginal_val;

}
```
<br>

```
let x= "6";
plusPlus(x); //7

```
<br>


What ++ operator is doing under the hood?

It is coercing orginal_val (i.e type:string)  to number and adding 1 with the coerced value and storing it in orginal_val and returning the increased orginal_val.




