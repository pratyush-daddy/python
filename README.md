












































### Q3 : Suppose you have a dataframe df with the following columns:

id: a unique identifier for each row<br>
group: a categorical variable with 3 possible values: 'A', 'B', or 'C'<br>
timestamp: a datetime object representing the time that each row was recorded<br>
value: a numerical value for each row<br>
Write a function get_top_n_values_by_group(df, n) that returns a dataframe with the top n values for each group, ordered by timestamp (earliest to latest). The resulting dataframe should have the same columns as the original dataframe.<br>

```python
df = pd.DataFrame({<br>
    'id': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15],<br>
    'group': ['A', 'A', 'A', 'B', 'B', 'B', 'C', 'C', 'C', 'A', 'B', 'C', 'A', 'C', 'C'],<br>
    'timestamp': pd.to_datetime(['2022-01-01 00:00:03', '2022-01-01 00:00:01', '2022-01-01 00:00:02',<br>
                                 '2022-01-01 00:00:04', '2022-01-01 00:00:02', '2022-01-01 00:00:01',<br>
                                 '2022-01-01 00:00:03', '2022-01-01 00:00:02', '2022-01-01 00:00:01',<br>
                                 '2022-01-01 00:00:04', '2022-01-01 00:00:03', '2022-01-01 00:00:02',<br>
                                 '2022-01-01 00:00:01', '2022-01-01 00:00:05', '2022-01-01 00:00:06']),<br>
    'value': [15, 20, 10, 22, 25, 18, 30, 28, 27, 12, 23, 26, 17,18,19]})
```    

### Solution :

```python

from IPython.display import display

def get_top_n_values_by_group(df, n):
    df.sort_values(by=['timestamp'])
    display(df.groupby('group').head(n))
    
df = pd.DataFrame({
    'id': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15],
    'group': ['A', 'A', 'A', 'B', 'B', 'B', 'C', 'C', 'C', 'A', 'B', 'C', 'A', 'C', 'C'],
    'timestamp': pd.to_datetime(['2022-01-01 00:00:03', '2022-01-01 00:00:01', '2022-01-01 00:00:02',
                                 '2022-01-01 00:00:04', '2022-01-01 00:00:02', '2022-01-01 00:00:01',
                                 '2022-01-01 00:00:03', '2022-01-01 00:00:02', '2022-01-01 00:00:01',
                                 '2022-01-01 00:00:04', '2022-01-01 00:00:03', '2022-01-01 00:00:02',
                                 '2022-01-01 00:00:01', '2022-01-01 00:00:05', '2022-01-01 00:00:06']),
    'value': [15, 20, 10, 22, 25, 18, 30, 28, 27, 12, 23, 26, 17,18,19]})

get_top_n_values_by_group(df, 2)

```
### Output :

| --- | id | group | timestamp | value |
| --- | --- | --- | --- | --- |
| 0 | 1 | A | 2022-01-01 00:00:03 | 15 |
| 1 | 2 | A | 2022-01-01 00:00:01 | 20 |
| 3 | 4 | B | 2022-01-01 00:00:04 | 22 |
| 4 | 5 | B | 2022-01-01 00:00:02 | 25 |
| 6 | 7 | C | 2022-01-01 00:00:03 | 30 |
| 7 | 8 | C | 2022-01-01 00:00:02 | 28 |

![dino](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWQzNmE4NWU5NzE5MDhlOTZjMTZiMmJmOWU1NjA3Yjk0NDhjZDEyYiZjdD1n/e18YuHVD6qOmtD8arr/giphy.gif)

### Q : Question: Given a DataFrame df with columns A, B, and C, write a function to return a new DataFrame with the following criteria:

The rows where A is greater than 5 <br>
The rows where B is between 10 and 20 (inclusive) <br>
The rows where C is not null <br>
The rows are sorted in descending order of A <br>

you can create dataframe based on your own assumption.

### Solution :

```python

data = {'A' : [13, 34, 11, 17, 12, np.nan, 45, 4],
        'B' : [25, 10, 15, 16, 12, 34, 11, 17],
        'C' : [56, np.nan, 45, 59, 69, 15, np.nan, 12]}

df = pd.DataFrame(data, columns=['A', 'B', 'C'])

print("The Given DataFrame is :\n", df, "\n")

new_df = df[(df['A'] > 5) & (df['B'] >=10) & (df['B'] <= 20) & (df['C'])].sort_values(by=['A'], ascending = False)

print("The New DataFrame is :\n", new_df)

```

### Output :

<table>
<tr><th>The Given DataFrame is :</th><th>The New DataFrame is :</th></tr>
<tr><td>

| |A|B|C|
|---|---|---|---|
|0 | 13.0 | 25 | 56.0 |
|1 | 34.0 | 10 | NaN |
|2 | 11.0 | 15 | 45.0 |
|3 | 17.0 | 16 | 59.0 |
|4 | 12.0 | 12 | 69.0 |
|5 | NaN | 34 | 15.0 |
|6 | 45.0 | 11 | NaN |
|7 | 4.0 | 17 | 12.0 |

</td><td>

| | A | B | C |
|---|---|---|---|
3 |  7.0 | 16 | 59.0
4 | 12.0 | 12 | 69.0
2 | 11.0 | 15 | 45.0

</td></tr> </table>

![dino](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWQzNmE4NWU5NzE5MDhlOTZjMTZiMmJmOWU1NjA3Yjk0NDhjZDEyYiZjdD1n/e18YuHVD6qOmtD8arr/giphy.gif)

### Q : You are required to write a program to sort the (name, age, score) tuples by ascending order where name is string, age and score are numbers. The tuples are input by console. The sort criteria is:

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
```yaml
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]
```

### Solution

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

```yaml
[('John', 20, 90), ('Jony', 17, 91), ('Jony', 17, 93), ('Json', 21, 85), ('Tom', 19, 80)]
```
 Note that the age and score values are integers in the sorted tuples, not strings as in the input tuples.
 
 The `key` argument in the `sorted` function takes a function that is used to extract a sorting key from each element in the input list.

In this case, the lambda function `lambda x: (x[0], x[1], x[2])` takes a single argument `x`, which is a tuple of three values (name, age, score).

The lambda function then returns a tuple `(x[0], x[1], x[2])`, which consists of the three values in the tuple `x`, in the order specified. This means that the tuples will be sorted primarily based on their first element (the name), then based on their second element (the age), and finally based on their third element (the score).

Using a tuple of values as the sorting key allows you to sort based on multiple criteria in a specific order of priority. In this case, the order of priority is name > age > score, so the lambda function returns a tuple that reflects this ordering.
