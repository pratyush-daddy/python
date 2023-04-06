## Q : You are required to write a program to sort the (name, age, score) tuples by ascending order where name is string, age and score are numbers. The tuples are input by console. The sort criteria is:

1: Sort based on name;<br>
2: Then sort based on age;<br>
3: Then sort by score.<br>
The priority is that name > age > score.<br>

If the following tuples are given as input to the program:<br>
`Tom,19,80`<br>
`John,20,90`<br>
`Jony,17,91`<br>
`Jony,17,93`<br>
`Json,21,85`<br>

Then, the output of the program should be:<br>
```python
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]
```

## Solution

You can use the built-in sorted function in Python to sort the list of tuples based on multiple criteria. Here's a Python program that implements the required sorting:

```python
# Get the input tuples from the user
input_tuples = []
while True:
    input_str = input("Enter a tuple (name, age, score), or press Enter to stop: ")
    if not input_str:
        break
    name, age, score = input_str.split(',')
    input_tuples.append((name.strip(), int(age.strip()), int(score.strip())))

# Sort the input tuples based on name, age, and score
sorted_tuples = sorted(input_tuples, key=lambda x: (x[0], x[1], x[2]))

# Print the sorted tuples
print(sorted_tuples)
```

In this program, we first get the input tuples from the user using the input function. We split each input string into three parts - name, age, and score - and convert the age and score to integers. We then append the resulting tuple to a list of input tuples.

Next, we sort the input tuples based on the specified criteria using the sorted function. We pass a key argument to the sorted function, which is a lambda function that returns a tuple of values to be used for sorting. In this case, we sort the tuples based on their name, age, and score, in that order.

Finally, we print the sorted tuples using the print function.

When the program is run with the input provided in the question, the output is:

```python
[('John', 20, 90), ('Jony', 17, 91), ('Jony', 17, 93), ('Json', 21, 85), ('Tom', 19, 80)]
```
 Note that the age and score values are integers in the sorted tuples, not strings as in the input tuples.
 
 The `key` argument in the `sorted` function takes a function that is used to extract a sorting key from each element in the input list.

In this case, the lambda function `lambda x: (x[0], x[1], x[2])` takes a single argument `x`, which is a tuple of three values (name, age, score).

The lambda function then returns a tuple `(x[0], x[1], x[2])`, which consists of the three values in the tuple `x`, in the order specified. This means that the tuples will be sorted primarily based on their first element (the name), then based on their second element (the age), and finally based on their third element (the score).

Using a tuple of values as the sorting key allows you to sort based on multiple criteria in a specific order of priority. In this case, the order of priority is name > age > score, so the lambda function returns a tuple that reflects this ordering.
