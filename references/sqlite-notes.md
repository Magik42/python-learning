# SQLite and the book tracker

These example notes describe `learning.ipynb` as it is currently written. Update them when the notebook changes.

## Where the data lives

`sqlite3.connect("books.db")` opens a database file or creates it if it does not exist. A relative filename is resolved from the notebook kernel's working directory.

The notebook uses `connection.commit()` to save its changes. `closing()` closes the connection when its block ends, including when an error occurs. Closing a connection does not commit pending changes.

## The books table

| Column | Purpose |
| --- | --- |
| `id` | An integer primary key that identifies a book. SQLite assigns it when omitted from an insert. |
| `title` | Required text containing the book title. |
| `author` | Text containing the author's name; it can be missing for existing personal entries. |
| `rating` | A required number between 0 and 5. |

The notebook contains 23 sample books with invented practice ratings. Rerunning it adds missing sample title-and-author pairs and preserves existing ratings. It also adds the author column to databases created by the earlier notebook.

## Reading data with a parameter

This example belongs inside the notebook's open connection block, before the connection closes:

```python
minimum_rating = 4.0
rows = connection.execute(
    """
    SELECT title, author, rating
    FROM books
    WHERE rating >= ?
    ORDER BY rating DESC, title
    """,
    (minimum_rating,),
).fetchall()
```

`SELECT` chooses columns. `WHERE` filters rows. `ORDER BY` sorts the result, and `DESC` means highest first.

The `?` is a placeholder for a value passed separately to SQLite. Keep using placeholders for values rather than building SQL with f-strings. The comma in `(minimum_rating,)` makes it a tuple with one item.

The notebook currently filters at 4.0. Changing the parameter to `(0.0,)` shows all books with valid ratings.
