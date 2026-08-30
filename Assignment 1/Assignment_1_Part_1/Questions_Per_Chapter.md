# Chapter 2 Questions

**Q:** What is the difference between single quotes and double quotes for strings?

**Q:** When should I use f-strings instead of regular strings?

**Q:** What is the purpose of `title()`, `upper()`, and `lower()` string methods?

**Q:** What does `\t` and `\n` do in a string?

**Q:** What is the difference between `strip()`, `lstrip()`, and `rstrip()`?

**Q:** How does integer division (`//`) differ from regular division (`/`)?

**Q:** What are comments in Python and when should I use them?

**Q:** What is the Zen of Python and why is it important?

**Q:** Why does `repr()` show quotes and escape characters?

**Q:** Why does `print(name.lower())` not change the original variable?

**Q:** Why does `print(5 + 3)` show `8` but `print("5" + "3")` shows `"53"`?

**Q:** Why is `//` called "floor division"? What does it do with negative numbers?

---

# Chapter 3 Questions

**Q:** What is a list and how is it different from a variable?

**Q:** How do I access individual elements in a list?

**Q:** What is negative indexing in Python lists?

**Q:** How do I add items to a list (append vs insert)?

**Q:** How do I remove items from a list (del vs pop vs remove)?

**Q:** What is the difference between `sort()` and `sorted()`?

**Q:** How does `reverse()` work on a list?

**Q:** What does `len()` return for a list?

**Q:** How do I create a copy of a list?

**Q:** Why does `my_list = original_list` NOT create a copy?

**Q:** What is the difference between `pop()` and `pop(0)`?

**Q:** Why does `sort()` return `None` instead of the sorted list?

**Q:** Why does `reverse()` change the list in place?

**Q:** What happens if you try to access an index that doesn't exist?

**T/F:** `append()` adds an item to the beginning of a list.

**T/F:** `insert(0, "item")` adds an item to the beginning of a list.

**T/F:** `remove()` deletes an item by its index.

**T/F:** `pop()` without an argument removes the last item.

**T/F:** `sorted()` modifies the original list.

**T/F:** `sort()` returns a new sorted list.

**T/F:** `my_list[:]` creates a copy of the list.

**T/F:** `my_list[-1]` accesses the last item.

---

# Chapter 4 Questions

**Q:** What is a for loop and how does it work with lists?

**Q:** What is the `range()` function and what does each argument do?

**Q:** How do I create a list of numbers using `range()`?

**Q:** What is the difference between `min()`, `max()`, and `sum()`?

**Q:** What is a list comprehension and when should I use it?

**Q:** What are slices and how do I use them to get parts of a list?

**Q:** How do I copy a list using slicing?

**Q:** What is a tuple and how is it different from a list?

**Q:** Why can't I modify a tuple?

**Q:** What is PEP 8 and why is it important?

**Q:** Why does `range(1, 21)` include 21?

**Q:** What does `[number ** 3 for number in range(1, 11)]` mean?

**Q:** Why does `cubes[-3:]` work but `cubes[3:-1]` might not?

**Q:** Why can't I do `menu[0] = "pizza"` on a tuple?

**Q:** What is the difference between `[:]` and `[::]` in slicing?

**T/F:** `range(1, 10)` includes the number 10.

**T/F:** `[x for x in range(5)]` is a list comprehension.

**T/F:** `cubes[1:4]` includes the item at index 4.

**T/F:** `cubes[-1]` returns the last item.

**T/F:** Tuples can be modified after creation.

**T/F:** `my_list[:]` creates a shallow copy.

**T/F:** `range(1, 21, 2)` produces even numbers.

**T/F:** `len()` works on both lists and tuples.

---

# Chapter 5 Questions

**Q:** What is a conditional statement?

**Q:** How do comparison operators work (`==`, `!=`, `<`, `>`, `<=`, `>=`)?

**Q:** What is the difference between `=` and `==`?

**Q:** How do `if`, `elif`, and `else` work together?

**Q:** What is the difference between `and` and `or`?

**Q:** How do I check if an item is in a list (`in` keyword)?

**Q:** How do I check if an item is NOT in a list (`not in` keyword)?

**Q:** What does `lower()` do in conditional comparisons?

**Q:** How do I check if a list is empty?

**Q:** Why does `if usernames:` work to check if a list is empty?

**Q:** What happens when multiple `if` statements are used instead of `elif`?

**Q:** Why does `"Hello" == "hello"` return `False`?

**Q:** What is short-circuit evaluation in `and`/`or`?

**Q:** Why does `if username.lower() in current_users_lower:` work?

**T/F:** `=` is used to check equality.

**T/F:** `==` is used to assign a value.

**T/F:** `if-elif-else` checks all conditions even after one is True.

**T/F:** `and` requires both conditions to be True.

**T/F:** `or` requires both conditions to be True.

**T/F:** `in` checks if an item exists in a list.

**T/F:** `not in` checks if an item does NOT exist in a list.

**T/F:** An empty list is considered "truthy".

**T/F:** `if usernames:` is the same as `if len(usernames) > 0:`.