# Book tracker exercises

These are optional practice examples, not completed lessons. Try one at a time, predict the result, and then run the notebook to compare.

## 1. Change the rating filter

Change the query parameter from `(4.0,)` to `(4.5,)`.

Expected result: every displayed book has a rating of at least 4.5. The saved ratings stay the same because a `SELECT` query only reads data.

Then try `(0.0,)` to see all books.

## 2. Sort by title

Replace `ORDER BY rating DESC, id` with `ORDER BY title`.

Expected result: the same matching books appear in title order.

## 3. Filter by author

Change the query condition to `WHERE author = ?` and pass `("George Orwell",)` as the parameter.

Expected result: the sample collection returns `1984` and `Animal Farm`.

## 4. Count the books

Inside the open connection block, try:

```python
book_count = connection.execute("SELECT COUNT(*) FROM books").fetchone()[0]
print(f"Books in the database: {book_count}")
```

Expected result: a database containing only the sample collection has 23 books. The count includes books below the display's rating filter.

## 5. Add your own book

Add one new `(title, author, rating)` tuple to `sample_books`, using a rating between 0 and 5. Run the cell twice.

Expected result: the book is saved once. Use the counting exercise to check it even if its rating is below the display filter.

Removing a tuple from `sample_books` does not delete the saved database row. Changing its sample rating does not update a row that is already saved; that requires an `UPDATE` query, which can be a later lesson.
