# Python notes

These example notes use the book tracker in `learning.ipynb`. Add your own notes as you learn.

## Variables

A variable gives a value a name so you can use it later.

```python
minimum_rating = 4.0
```

Use names that explain the value, such as `minimum_rating` instead of `x`.

## Lists and tuples

A list holds several items. In the notebook, each book is a tuple containing a title, an author, and a rating.

```python
books = [
    ("The Hobbit", "J. R. R. Tolkien", 4.8),
    ("Frankenstein", "Mary Shelley", 4.2),
]
```

Square brackets create a list. Parentheses group the values in each tuple.

## Loops and unpacking

A `for` loop repeats an action for each item. Unpacking assigns the values from a tuple to separate names.

```python
for title, author, rating in books:
    print(f"{title} by {author}: {rating:.1f}/5")
```

The indented line runs once per book. The `f` before the string lets you insert values using braces. `:.1f` displays a number with one decimal place.

## Notebook cells

Code cells run Python. Markdown cells contain explanations.

A notebook remembers variables from previously run cells. Use **Restart Kernel**, then **Run All**, to check whether the notebook works from the beginning. Restarting clears Python variables; it does not delete the saved `books.db` file.
