# Recursion
```js
1.| function countEvenToTwelve(number) {
2.|   if (number <= 12) { // Recursive Case
3.|     console.log(number);
4.|     // The function will call itself again and get closer to the base case
5.|     countEvenToTwelve(number+2);
6.|   }
7.|   // Base case, do nothing when number > 12
8.| }
9.| countEvenToTwelve(0);
```
`countEvenToTwelve` function will continue to call itself as long as number `<= 12`; so as soon as number `> 12`, the function will no longer call itself. If we didn't have the if statement in there, the function would call itself forever and would not be a valid recursive function. Every recursive function must stop calling itself at some point.

* We refer to number <= 12 as a recursive case, because as long as this is true, the function will continue to call itself.
* We refer to number > 12 as a **base case**. If this is true, the function will not call itself.

The recursive case is when the function will continue to call itself. Every time the function calls itself, the input gets closer and closer to the **base case**. The base case is when the function no longer calls itself. 