# coding exercises -- and the way dunn solves them

(i'm using javascript here but i can switch to python if you'd rather)

for reference:
```
// arrays
someArray[0] = 'a';        // assigns the value 'a' to the first element in the array
someArray[4];              // return the value found at position 4 in someArray. [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
	                                                                                  //  ^4th position
```

## 1. reverse a string

**problem:** given a string, write a program that will reverse it and print it to standard out.

```
/*-- start from here --*/
const inputString = 'wizard';
```

### breakdown:
first off, i look at the problem and break it up into small parts. this more or less happens automatically for me at this point but it's a good practice to get into.
- we have one string
- we have to reverse it
- we have to print it out.

now i start thinking about how to write an algorithm to solve the problem
- reversing a string is basically moving each letter of a string to another place in the string, 
  and since we need to touch every letter (keyword: EVERY) i know we can use a loop.
- loops can either "go forward" or "go backward" in a sense. if you look at a basic for loop as you've learned it, it takes three arguments to create"
	an iterator variable, a conditional boolean expression, and an expression that will happen once every loop.
	e.g. (just used 5000 as an example here): 
	```
	for (let i = 0; i < 5000; i++) {
		// this will run 5000 times because i starts at 0, increments every loop (i++), and the loop condition is no longer true when i = 5000 (i < 5000)
	}
	```

in this example i consider this loop as "going forward" because our iterator variable is increasing and if
we wanted to say iterate over a string (walk through a string letter by letter) we can use this to our advantage BECAUSE:
	a string is just an array. say our string is "wizard", that's pretty much just an array with some other fancy functions and attributes on it.
	it really looks like this: inputString = ['w', 'i', 'z', 'a', 'r', 'd'], with each letter/element corresponding to a specific position number within the array.
	which start from 0 and increase from there: `inputString[0] == 'w'`, `inputString[4] == 'r'`, etc.

SO, knowing this we can step through our string letter by letter using our loop since i is increasing with every loop!
but wait, if we want to reverse the string, wouldn't it be easier if we started back to front? that way we can just grab the letters in reverse order.
let's change the loop so rather than increasing i it decreases i! but to make this useful we'll want our i to start at the last letter, i = inputString.length - 1 (- 1 here because since the positions start from 0 the length of the string is always going to be 1 more than our position). we'll also want to change our condition so that it stops when we've hit the first letter, i >= 0 OR i > -1, whichever you prefer

let's put it all together!

```
const inputString = 'wizard';

let reversed = ''; // create an empty string to store our end result! i define it outside of the loop because we'll be adding to it letter by letter

for (let i = inputString.length - 1; i >= 0; i--) {
	let currentLetter = inputString[i]; // this gets us a new letter each loop cycle because i keeps decreasing!

	// this is the same as writing reversed = reversed + currentLetter. basically it's taking the current value of reversed and adding currentLetter to the end of it and then overwriting reversed with that new value
	reversed += currentLetter;
}

console.log(reversed);
```
