## Chapter 6 Questions

**Q:** What is the difference between a dictionary and a list in Python?

**Q:** How does `.items()` work, and why do we use two variables (`key, value`) in the for loop?

**Q:** What does `.title()` do to a string, and why do we use it when printing names?

**Q:** If a dictionary has keys `"first_name"` and `"First_Name"`, are they the same key? Why or why not?

**Q:** What happens if you try to access a key that doesn't exist in a dictionary, like `person["middle_name"]`?

**Q:** Can you modify a dictionary's value after creating it? How?

**T/F:** Dictionaries are ordered by default in Python 3.7+.

**T/F:** `person["first_name"]` and `person.first_name` are both valid ways to access dictionary values.

**T/F:** `.keys()` returns a list of all the values in a dictionary.

**T/F:** You can change a dictionary value by reassigning it: `person["age"] = 31`.

**T/F:** Dictionary keys must be unique — you cannot have two identical keys.

---

## Chapter 7 Questions

**Q:** What is the difference between a `for` loop and a `while` loop? When would you use each?

**Q:** Why do we use `input()` to get user input, and what does it always return?

**Q:** What does the `break` statement do, and where does it exit from?

**Q:** What is an "active variable" pattern, and why is it useful?

**Q:** Why does `while True:` create an infinite loop, and how do you safely stop it?

**Q:** What is the difference between `pop()` and `pop(0)` on a list?

**Q:** What does `.remove()` do, and how is it different from `pop()`?

**Q:** Why do we check `if "pastrami" in sandwich_orders:` before removing it?

**T/F:** `input()` always returns a string, even if the user types a number.

**T/F:** A `while` loop will stop automatically when its condition becomes False.

**T/F:** `break` exits the entire loop, while `continue` skips to the next iteration.

**T/F:** `pop(0)` removes and returns the first item in a list.

**T/F:** `remove()` deletes an item by its index position.

**T/F:** `while topping != "quit":` will run forever if `topping` never changes.

**T/F:** The `in` keyword can be used to check if a value exists in a list.

---

## Chapter 8 Questions

**Q:** What is a function, and why is it useful to define one?

**Q:** What is the difference between a parameter and an argument?

**Q:** What does `return` do, and how is it different from `print()`?

**Q:** What are positional arguments, and why does order matter?

**Q:** What are keyword arguments, and how do they differ from positional arguments?

**Q:** What does it mean when a parameter has a default value, like `size="large"`?

**Q:** What does `*items` do in a function definition, and what type does it create inside the function?

**Q:** What does `**user_info` do, and what type does it create inside the function?

**Q:** How does `car.update(car_info)` work when `car_info` is a dictionary from `**kwargs`?

**Q:** What is the difference between `import module_name` and `from module_name import function_name`?

**T/F:** A function must always have a `return` statement.

**T/F:** `return` sends a value back to where the function was called.

**T/F:** Default parameter values are used when the caller doesn't provide that argument.

**T/F:** `def make_shirt(size, message="I love Python"):` requires both arguments.

**T/F:** `*items` collects extra positional arguments into a tuple.

**T/F:** `**user_info` collects extra keyword arguments into a dictionary.

**T/F:** `print()` displays text, while `return` gives a value back to the code that called the function.

**T/F:** You can call a function before it is defined in the same file, as long as it's defined before the code runs.

---

## Chapter 9 Questions

**Q:** What is a class, and how is it different from a function?

**Q:** What is the purpose of `__init__()` in a class?

**Q:** What does `self` refer to inside a class method?

**Q:** What is the difference between an attribute and a method?

**Q:** What is an instance (or object) of a class?

**Q:** How does inheritance work, and what does `super().__init__()` do?

**Q:** Why do we use `super()` when creating a child class?

**T/F:** A class is a blueprint, and an instance is the actual object created from that blueprint.

**T/F:** `self` is automatically passed as the first argument when you call a method on an instance.

**T/F:** Attributes defined in `__init__()` belong to the class itself, not individual instances.

**T/F:** A child class inherits all methods and attributes from its parent class.

**T/F:** `super().__init__()` calls the parent class's `__init__()` method.

**T/F:** You can add new methods to a child class that the parent class doesn't have.

---

## Chapter 10 Questions

**Q:** What does the `with open(...) as file:` pattern do, and why is it recommended?

**Q:** What is the difference between `"r"`, `"w"`, and `"a"` file modes?

**Q:** What does `.read()` return, and what type is it?

**Q:** What is the difference between `.read()` and `.readlines()`?

**Q:** What does a `try-except` block do, and when would you use it?

**Q:** What is `FileNotFoundError`, and how do you handle it?

**T/F:** `"w"` mode will overwrite an existing file without warning.

**T/F:** `"a"` mode appends to the end of an existing file.

**T/F:** `.readlines()` returns a list of strings, one for each line in the file.

**T/F:** The `with` statement automatically closes the file when the block ends.

**T/F:** `json.dump()` converts Python data into a JSON string and writes it to a file.

**T/F:** `json.load()` reads JSON data from a file and converts it back to Python objects.

**T/F:** `os.path.exists()` returns `True` if a file exists, and `False` otherwise.

**T/F:** `try-except` blocks are only used for file operations.