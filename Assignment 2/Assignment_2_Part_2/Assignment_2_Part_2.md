# Assignment 2

## Chapter 6: Dictionaries

### Try It Yourself

**6-1. Person**  
Use a dictionary to store information about a person you know. Store their first name, last name, age, and the city in which they live. You should have keys such as `first_name`, `last_name`, `age`, and `city`. Print each piece of information stored in your dictionary.

---

**6-2. Favorite Numbers**  
Use a dictionary to store people's favorite numbers. Think of five names, and use them as keys in your dictionary. Think of a favorite number for each person, and store each as a value in your dictionary. Print each person's name and their favorite number. For even more fun, poll a few friends and get some actual data for your program.

---

**6-3. Glossary**  
A Python dictionary can be used to model an actual dictionary. However, to avoid confusion, let's call it a glossary.

- Think of five programming words you've learned about in the previous chapters. Use these words as the keys in your glossary, and store their meanings as values.
- Print each word and its meaning as neatly formatted output. You might print the word followed by a colon and then its meaning, or print the word on one line and then print its meaning indented on a second line. Use the newline character (`\n`) to insert a blank line between each word-meaning pair in your output.

---

**6-4. Glossary 2**  
Now that you know how to loop through a dictionary, clean up the code from Exercise 6-3 by replacing your series of `print()` calls with a loop that runs through the dictionary's keys and values. When you're sure that your loop works, add five more Python terms to your glossary. When you run your program again, these new words and meanings should automatically be included in the output.

---

**6-5. Rivers**  
Make a dictionary containing three major rivers and the country each river runs through. One key-value pair might be `'nile': 'egypt'`.

- Use a loop to print a sentence about each river, such as *The Nile runs through Egypt.*
- Use a loop to print the name of each river included in the dictionary.
- Use a loop to print the name of each country included in the dictionary.

---

**6-6. Polling**  
Use the code in `favorite_languages.py` (page 97).

- Make a list of people who should take the favorite languages poll. Include some names that are already in the dictionary and some that are not.
- Loop through the list of people who should take the poll. If they have already taken the poll, print a message thanking them for responding. If they have not yet taken the poll, print a message inviting them to take the poll.

---

**6-7. People**  
Start with the program you wrote for Exercise 6-1 (page 99). Make two new dictionaries representing different people and store all three dictionaries in a list called `people`. Loop through your list of people. As you loop through the list, print everything you know about each person.

---

**6-8. Pets**  
Make several dictionaries, where each dictionary represents a different pet. In each dictionary, include the kind of animal and the owner's name. Store these dictionaries in a list called `pets`. Next, loop through your list and as you do, print everything you know about each pet.

---

**6-9. Favorite Places**  
Make a dictionary called `favorite_places`. Think of three names to use as keys in the dictionary, and store one to three favorite places for each person. To make this exercise a bit more interesting, ask some friends to name a few of their favorite places. Loop through the dictionary and print each person's name and their favorite places.

---

**6-10. Favorite Numbers**  
Modify your program from Exercise 6-2 (page 99) so each person can have more than one favorite number. Then print each person's name along with their favorite numbers.

---

**6-11. Cities**  
Make a dictionary called `cities`. Use the names of three cities as keys in your dictionary. Create a dictionary of information about each city and include the country that the city is in, its approximate population, and one fact about that city. The keys for each city's dictionary should be something like `country`, `population`, and `fact`. Print the name of each city and all of the information you have stored about it.

---

**6-12. Extensions**  
We're now working with examples that are complex enough that they can be extended in any number of ways. Use one of the example programs from this chapter, and extend it by adding new keys and values, changing the context of the program, or improving the formatting of the output.

---

## Chapter 7: User Input and while Loops

### Try It Yourself

**7-1. Rental Car**  
Write a program that asks the user what kind of rental car they would like. Print a message about that car, such as *"Let me see if I can find you a Subaru."*

---

**7-2. Restaurant Seating**  
Write a program that asks the user how many people are in their dinner group. If the answer is more than eight, print a message saying they'll have to wait for a table. Otherwise, report that their table is ready.

---

**7-3. Multiples of Ten**  
Ask the user for a number, and then report whether the number is a multiple of 10 or not.

---

**7-4. Pizza Toppings**  
Write a loop that prompts the user to enter a series of pizza toppings until they enter a `'quit'` value. As they enter each topping, print a message saying you'll add that topping to their pizza.

---

**7-5. Movie Tickets**  
A movie theater charges different ticket prices depending on a person's age. If a person is under the age of 3, the ticket is free; if they are between 3 and 12, the ticket is $10; and if they are over age 12, the ticket is $15. Write a loop in which you ask users their age and then tell them the cost of their movie ticket.

---

**7-6. Three Exits**  
Write different versions of either Exercise 7-4 or Exercise 7-5 that do each of the following at least once:

- Use a conditional test in the `while` statement to stop the loop.
- Use an active variable to control how long the loop runs.
- Use a `break` statement to exit the loop when the user enters a `'quit'` value.

---

**7-7. Infinity**  
Write a loop that never ends and run it. (To end the loop, press `Ctrl+C` or close the window displaying the output.)

---

**7-8. Deli**  
Make a list called `sandwich_orders` and fill it with the names of various sandwiches. Then make an empty list called `finished_sandwiches`. Loop through the list of sandwich orders and print a message for each order, such as *I made your tuna sandwich.* As each sandwich is made, move it to the list of finished sandwiches. After all the sandwiches have been made, print a message listing each sandwich that was made.

---

**7-9. No Pastrami**  
Using the list `sandwich_orders` from Exercise 7-8, make sure the sandwich `'pastrami'` appears in the list at least three times. Add code near the beginning of your program to print a message saying the deli has run out of pastrami, and then use a `while` loop to remove all occurrences of `'pastrami'` from `sandwich_orders`. Make sure no pastrami sandwiches end up in `finished_sandwiches`.

---

**7-10. Dream Vacation**  
Write a program that polls users about their dream vacation. Write a prompt similar to *If you could visit one place in the world, where would you go?* Include a block of code that prints the results of the poll.

---

## Chapter 8: Functions

### Try It Yourself

**8-1. Message**  
Write a function called `display_message()` that prints one sentence telling everyone what you are learning about in this chapter. Call the function, and make sure the message displays correctly.

---

**8-2. Favorite Book**  
Write a function called `favorite_book()` that accepts one parameter, `title`. The function should print a message, such as *One of my favorite books is Alice in Wonderland.* Call the function, making sure to include a book title as an argument in the function call.

---

**8-3. T-Shirt**  
Write a function called `make_shirt()` that accepts a size and the text of a message that should be printed on the shirt. The function should print a sentence summarizing the size of the shirt and the message printed on it. Call the function once using positional arguments to make a shirt. Call the function a second time using keyword arguments.

---

**8-4. Large Shirts**  
Modify the `make_shirt()` function so that shirts are large by default with a message that reads *I love Python.* Make a large shirt and a medium shirt with the default message, and a shirt of any size with a different message.

---

**8-5. Cities**  
Write a function called `describe_city()` that accepts the name of a city and its country. The function should print a simple sentence, such as *Reykjavik is in Iceland.* Give the parameter for the country a default value. Call your function for three different cities, at least one of which is not in the default country.

---

**8-6. City Names**  
Write a function called `city_country()` that takes in the name of a city and its country. The function should return a string formatted like this: `"Santiago, Chile"`. Call your function with at least three city-country pairs, and print the values that are returned.

---

**8-7. Album**  
Write a function called `make_album()` that builds a dictionary describing a music album. The function should take in an artist name and an album title, and it should return a dictionary containing these two pieces of information. Use the function to make three dictionaries representing different albums. Print each return value to show that the dictionaries are storing the album information correctly.

Use `None` to add an optional parameter to `make_album()` that allows you to store the number of songs on an album. If the calling line includes a value for the number of songs, add that value to the album's dictionary. Make at least one new function call that includes the number of songs on an album.

---

**8-8. User Albums**  
Start with your program from Exercise 8-7. Write a `while` loop that allows users to enter an album's artist and title. Once you have that information, call `make_album()` with the user's input and print the dictionary that's created. Be sure to include a quit value in the while loop.

---

**8-9. Messages**  
Make a list containing a series of short text messages. Pass the list to a function called `show_messages()`, which prints each text message.

---

**8-10. Sending Messages**  
Start with a copy of your program from Exercise 8-9. Write a function called `send_messages()` that prints each text message and moves each message to a new list called `sent_messages` as it's printed. After calling the function, print both of your lists to make sure the messages were moved correctly.

---

**8-11. Archived Messages**  
Start with your work from Exercise 8-10. Call the function `send_messages()` with a copy of the list of messages. After calling the function, print both of your lists to show that the original list has retained its messages.

---

**8-12. Sandwiches**  
Write a function that accepts a list of items a person wants on a sandwich. The function should have one parameter that collects as many items as the function call provides, and it should print a summary of the sandwich that's being ordered. Call the function three times, using a different number of arguments each time.

---

**8-13. User Profile**  
Start with a copy of `user_profile.py` from page 149. Build a profile of yourself by calling `build_profile()`, using your first and last names and three other key-value pairs that describe you.

---

**8-14. Cars**  
Write a function that stores information about a car in a dictionary. The function should always receive a manufacturer and a model name. It should then accept an arbitrary number of keyword arguments. Call the function with the required information and two other name-value pairs, such as a color or an optional feature. Your function should work for a call like this one:

```python
car = make_car('subaru', 'outback', color='blue', tow_package=True)
```

Print the dictionary that's returned to make sure all the information was stored correctly.

---

**8-15. Printing Models**  
Put the functions for the example `printing_models.py` in a separate file called `printing_functions.py`. Write an `import` statement at the top of `printing_models.py`, and modify the file to use the imported functions.

---

**8-16. Imports**  
Using a program you wrote that has one function in it, store that function in a separate file. Import the function into your main program file, and call the function using each of these approaches:

```python
import module_name
from module_name import function_name
from module_name import function_name as fn
import module_name as mn
from module_name import *
```

---

**8-17. Styling Functions**  
Choose any three programs you wrote for this chapter, and make sure they follow the styling guidelines described in this section.

---

## Chapter 9: Classes

### Try It Yourself

**9-1. Restaurant**  
Make a class called `Restaurant`. The `__init__()` method for `Restaurant` should store two attributes: a `restaurant_name` and a `cuisine_type`. Make a method called `describe_restaurant()` that prints these two pieces of information, and a method called `open_restaurant()` that prints a message indicating that the restaurant is open.

Make an instance called `restaurant` from your class. Print the two attributes individually, and then call both methods.

---

**9-2. Three Restaurants**  
Start with your class from Exercise 9-1. Create three different instances from the class, and call `describe_restaurant()` for each instance.

---

**9-3. Users**  
Make a class called `User`. Create two attributes called `first_name` and `last_name`, and then create several other attributes that are typically stored in a user profile. Make a method called `describe_user()` that prints a summary of the user's information. Make another method called `greet_user()` that prints a personalized greeting to the user.

Create several instances representing different users, and call both methods for each user.

---

**9-4. Number Served**  
Start with your program from Exercise 9-1 (page 162). Add an attribute called `number_served` with a default value of `0`. Create an instance called `restaurant` from this class. Print the number of customers the restaurant has served, and then change this value and print it again.

Add a method called `set_number_served()` that lets you set the number of customers that have been served. Call this method with a new number and print the value again.

Add a method called `increment_number_served()` that lets you increment the number of customers who've been served. Call this method with any number you like that could represent how many customers were served in, say, a day of business.

---

**9-5. Login Attempts**  
Add an attribute called `login_attempts` to your `User` class from Exercise 9-3 (page 162). Write a method called `increment_login_attempts()` that increments the value of `login_attempts` by `1`. Write another method called `reset_login_attempts()` that resets the value of `login_attempts` to `0`.

Make an instance of the `User` class and call `increment_login_attempts()` several times. Print the value of `login_attempts` to make sure it was incremented properly, and then call `reset_login_attempts()`. Print `login_attempts` again to make sure it was reset to `0`.

---

**9-6. Ice Cream Stand**  
An ice cream stand is a specific kind of restaurant. Write a class called `IceCreamStand` that inherits from the `Restaurant` class you wrote in Exercise 9-1 (page 162) or Exercise 9-4 (page 167). Either version of the class will work; just pick the one you like better. Add an attribute called `flavors` that stores a list of ice cream flavors. Write a method that displays these flavors. Create an instance of `IceCreamStand`, and call this method.

---

**9-7. Admin**  
An administrator is a special kind of user. Write a class called `Admin` that inherits from the `User` class you wrote in Exercise 9-3 (page 162) or Exercise 9-5 (page 167). Add an attribute, `privileges`, that stores a list of strings like `"can add post"`, `"can delete post"`, `"can ban user"`, and so on. Write a method called `show_privileges()` that lists the administrator's set of privileges. Create an instance of `Admin`, and call your method.

---

**9-8. Privileges**  
Write a separate `Privileges` class. The class should have one attribute, `privileges`, that stores a list of strings as described in Exercise 9-7. Move the `show_privileges()` method to this class. Make a `Privileges` instance as an attribute in the `Admin` class. Create a new instance of `Admin` and use your method to show its privileges.

---

**9-9. Battery Upgrade**  
Use the final version of `electric_car.py` from this section. Add a method to the `Battery` class called `upgrade_battery()`. This method should check the battery size and set the capacity to `100` if it isn't already. Make an electric car with a default battery size, call `get_range()` once, and then call `get_range()` a second time after upgrading the battery. You should see an increase in the car's range.

---

**9-10. Imported Restaurant**  
Using your latest `Restaurant` class, store it in a module. Make a separate file that imports `Restaurant`. Make a `Restaurant` instance, and call one of `Restaurant`'s methods to show that the import statement is working properly.

---

**9-11. Imported Admin**  
Start with your work from Exercise 9-8 (page 173). Store the classes `User`, `Privileges`, and `Admin` in one module. Create a separate file, make an `Admin` instance, and call `show_privileges()` to show that everything is working correctly.

---

**9-12. Multiple Modules**  
Store the `User` class in one module, and store the `Privileges` and `Admin` classes in a separate module. In a separate file, create an `Admin` instance and call `show_privileges()` to show that everything is still working correctly.

---

**9-13. Dice**  
Make a class `Die` with one attribute called `sides`, which has a default value of `6`. Write a method called `roll_die()` that prints a random number between `1` and the number of sides the die has. Make a 6-sided die and roll it 10 times.

Make a 10-sided die and a 20-sided die. Roll each die 10 times.

---

**9-14. Lottery**  
Make a list or tuple containing a series of 10 numbers and five letters. Randomly select four numbers or letters from the list and print a message saying that any ticket matching these four numbers or letters wins a prize.

---

**9-15. Lottery Analysis**  
You can use a loop to see how hard it might be to win the kind of lottery you just modeled. Make a list or tuple called `my_ticket`. Write a loop that keeps pulling numbers until your ticket wins. Print a message reporting how many times the loop had to run to give you a winning ticket.

---

**9-16. Python Module of the Week**  
One excellent resource for exploring the Python standard library is a site called Python Module of the Week. Go to [https://pymotw.com/](https://pymotw.com/) and look at the table of contents. Find a module that looks interesting to you and read about it, perhaps starting with the `random` module.

---

## Chapter 10: Files and Exceptions

### Try It Yourself

**10-1. Learning Python**  
Open a blank file in your text editor and write a few lines summarizing what you've learned about Python so far. Start each line with the phrase *In Python you can...* Save the file as `learning_python.txt` in the same directory as your exercises from this chapter. Write a program that reads the file and prints what you wrote three times. Print the contents once by reading in the entire file, once by looping over the file object, and once by storing the lines in a list and then working with them outside the `with` block.

---

**10-2. Learning C**  
You can use the `replace()` method to replace any word in a string with a different word. Here's a quick example showing how to replace `'dog'` with `'cat'` in a sentence:

```python
>>> message = "I really like dogs."
>>> message.replace('dog', 'cat')
'I really like cats.'
```

Read in each line from the file you just created, `learning_python.txt`, and replace the word *Python* with the name of another language, such as *C*. Print each modified line to the screen.

---

**10-3. Guest**  
Write a program that prompts the user for their name. When they respond, write their name to a file called `guest.txt`.

---

**10-4. Guest Book**  
Write a `while` loop that prompts users for their name. When they enter their name, print a greeting to the screen and add a line recording their visit in a file called `guest_book.txt`. Make sure each entry appears on a new line in the file.

---

**10-5. Programming Poll**  
Write a `while` loop that asks people why they like programming. Each time someone enters a reason, add their reason to a file that stores all the responses.

---

**10-6. Addition**  
One common problem when prompting for numerical input occurs when people provide text instead of numbers. When you try to convert the input to an `int`, you'll get a `ValueError`. Write a program that prompts for two numbers. Add them together and print the result. Catch the `ValueError` if either input value is not a number, and print a friendly error message. Test your program by entering two numbers and then by entering some text instead of a number.

---

**10-7. Addition Calculator**  
Wrap your code from Exercise 10-6 in a `while` loop so the user can continue entering numbers even if they make a mistake and enter text instead of a number.

---

**10-8. Cats and Dogs**  
Make two files, `cats.txt` and `dogs.txt`. Store at least three names of cats in the first file and three names of dogs in the second file. Write a program that tries to read these files and print the contents of the file to the screen. Wrap your code in a `try-except` block to catch the `FileNotFound` error, and print a friendly message if a file is missing. Move one of the files to a different location on your system, and make sure the code in the `except` block executes properly.

---

**10-9. Silent Cats and Dogs**  
Modify your `except` block in Exercise 10-8 to fail silently if either file is missing.

---

**10-10. Common Words**  
Visit [Project Gutenberg](https://gutenberg.org/) and find a few texts you'd like to analyze. Download the text files for these works, or copy the raw text from your browser into a text file on your computer.

You can use the `count()` method to find out how many times a word or phrase appears in a string. For example, the following code counts the number of times `'row'` appears in a string:

```python
>>> line = "Row, row, row your boat"
>>> line.count('row')
2
>>> line.lower().count('row')
3
```

Notice that converting the string to lowercase using `lower()` catches all appearances of the word you're looking for, regardless of how it's formatted.

Write a program that reads the files you found at Project Gutenberg and determines how many times the word `'the'` appears in each text. This will be an approximation because it will also count words such as `'then'` and `'there'`. Try counting `'the '`, with a space in the string, and see how much lower your count is.

---

**10-11. Favorite Number**  
Write a program that prompts for the user's favorite number. Use `json.dump()` to store this number in a file. Write a separate program that reads in this value and prints the message, *"I know your favorite number! It's _____."*

---

**10-12. Favorite Number Remembered**  
Combine the two programs from Exercise 10-11 into one file. If the number is already stored, report the favorite number to the user. If not, prompt for the user's favorite number and store it in a file. Run the program twice to see that it works.

---

**10-13. Verify User**  
The final listing for `remember_me.py` assumes either that the user has already entered their username or that the program is running for the first time. We should modify it in case the current user is not the person who last used the program.

Before printing a welcome back message in `greet_user()`, ask the user if this is the correct username. If it's not, call `get_new_username()` to get the correct username.

---
