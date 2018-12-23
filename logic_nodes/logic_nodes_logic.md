# Logic

## Alternate

Alternates between its activated outputs to pass through its input when it is being re-activated.  

![](/assets/Alternate.JPG)


## Array loop

It loops through each item assigned in an array."Value" give item specified by index's value."Done" calls connectors when it is done looping through the array.

![](/assets/array-loop.JPG)


## Branch

When activated, activates its "True" or "False" output, according to the state of the plugged-in boolean.

![](/assets/Branch.JPG)


## Gate

Logic nodes way to do "if" statements. When activated, it compares if its two inputs are being Equal, Greater Equal, Less Equal, or Not Equal, regardless of variable type, and passes through its red input if the set state is the case.

"And" and "Or" are being used for booleans only, and pass through the input when both bools are true \(and\) or at least one \(or\).

![](/assets/Gate.JPG)


## Inverse

Bool will become opposite, True will become False, False will become True.

![](/assets/Inverse.JPG)


## Is True/False

Passes through its activation only if the plugged in boolean is "True"/"False", according to the node.

![](/assets/Is-true_false.JPG)


## Is None

Give bool value of null i.e., If it is null then its output true(Doesn't have value), if it is not null then it outputs false(Have value).

![](/assets/is-none.JPG)


## Is Not None

Give opposite bool value of null i.e., If it is not null then its output true(Have value), if it is null then it output false(Doesn't have value).

![](/assets/is-not-none.JPG)


## Loop

It is basically for(i in from...to) loop. "Index" give value specified by the index value."Done" is called when it is done looping.

![](/assets/Loop.JPG)


## Loop Break

Loop Break terminates loop containing it.

![](/assets/loop-break.JPG)


## Merge

The "New" button creates new inputs, the "X" one deletes the most bottom one. If it receives on activation from any of its inputs, it will activate its output.

![](/assets/Merge.JPG)


## Not

Inverts a plugged in boolean, so if its input is "true" it outputs "false".

![](/assets/Not.JPG)


## Sequence

Its call output in sequential order.

![](/assets/Sequence.JPG)


## Switch

Check the value on input “in”, When the input value matches Case1, Case 2 or Case 3 value, it will trigger the corresponding output Case 1, Case 2 or Case 3. Click "new" to add more Case Value.

![](/assets/Switch.JPG)


## To Bool

Is false when there is no event on input, true when there is an event on input.

![](/assets/to-bool.JPG)


## While

Its loop through as long as bool specified in "Condition" is same.(i.e., like  while(jumping == true){do domething}).

![](/assets/While.JPG)


## Sleep

Activates the node connected with its output after the float value in seconds after it was activated itself.

![](/assets/sleep.JPG)