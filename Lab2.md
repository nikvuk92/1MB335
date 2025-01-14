# Session 2 - Python
In this lab, you will get an introduction to the programming language Python and how you can use it to do common tasks in Bioinformatics.
We recommend to do this on your own computer. UNIX distributions use to come with python already installed and accessible through the terminal, 
but you won't have any programming assistance tools. It's preferable for you to use some programming or data-analysis oriented text-editor instead, like Spyder, Jupyter or VSCode.
## Introduction 

The Wikipedia article for Python has the following to say about it:

```
Python is an interpreted, high-level, general-purpose programming language.
Created by Guido van Rossum and first released in 1991, Python's design philosophy emphasizes code readability with its notable use of significant whitespace.
Its language constructs and object-oriented approach aim to help programmers write clear, logical code for small and large-scale projects.[27]

Python is dynamically typed and garbage-collected.
It supports multiple programming paradigms, including procedural, object-oriented, and functional programming.
Python is often described as a "batteries included" language due to its comprehensive standard library.[28] 

```
https://en.wikipedia.org/wiki/Python\_(programming\_language)


As you might have gathered from the above excerpt, Python has an explicit goal of readability. The use of indentation to denote code blocks forces the programmer to properly indent their code. Take a look at the example below:

```
if True:
   print("True")
else:
   print("False")
```
as compared to the code below which will result in an error:

```
if True:
print "Answer"
print "True"
else:
print "Answer"
print "False"
```

In many other programming languages (such as Java & C) `;` denotes a linebreak. While it is possible to use it in Python the preferred way of denoting a new line is simply a text line break (i.e. hitting enter on your keyboard).

If you feel confident in your python skills then you can skip straight to question 1 below, if not then have a read through of the short introduction to python below:

### Hello world

Now it's time for you to write your first Python program. We will start with the iconic "Hello world".
Create a file in which you call the inbuilt `print` function with the text "Hello World".
Save the below text to a file (hello.py): 

```
print("hello world")
```
Now call it:

```
python hello.py
```


### Datatypes 
There are three types of numeric data in Python:

```
Integer: Positive or negative whole numbers
Float: A fraction of some type, i.e 0.5
Complex number: A number with a real and imaginary component represented as x+yj. x and y are floats and j is -1(square root of -1 called an imaginary number)
```

Integer and float are the only two we need to care about right now.

Open the Python interpreter (type `python` in the terminal) and try the following out:

```
>>> x = 4
>>> y = 5
>>> x+y
9
>>> x/y
0.8
```
We can use the inbuilt `type` function to see what types of data the above things are:

```
>>> type(x)
<class 'int'>
>>> type(x/y)
<class 'float'>
```

The next type of data are booleans, i.e. `True` or `False` (note the capital letters).

Next, we have sequence types:

```
String: A string value is a collection of one or more characters put in single, double, or triple quotes. 
List: A list object is an ordered collection of one or more data items, not necessarily of the same type, put in square brackets.
Tuple: A Tuple object is an ordered collection of one or more data items, not necessarily of the same type, put in parentheses.
```

Strings are, as you can see, just characters, such as our "Hello world" example above. 

They can be assigned as such:

```
my_string = "Hello"
```
And lists:

```
my_list = ['Hello', 'world']
```

Both lists and strings can be sliced and indexed:

```
>>>my_string[0]
'H'
>>>my_list[0]
'Hello'
```

As you can see Python is 0 indexed. 
You can use `[-1]` to get the last item of a list or string, and `[-2]` to get the second last et cetera.  
It is even possible to access intervals (ranges) of indexes. This is used with the colon `:`. For instance...

```
my_string[:-1]
```
... returns everything except the last index. 

```
my_string[1:-1]
```
... returns everything except the first and last index. 

Python lists contain many unbuilt methods for interacting with lists. As they are mutable it's possible to add and remove items. Such methods are called on the list with dot (`.`) notation as such:


|Method | Description|
---|:---|
|.append()|    Adds an element at the end of the list|
|.clear()|    Removes all the elements from the list|
|.copy()|        Returns a copy of the list|
|.count()|    Returns the number of elements with the specified value|
|.extend()|    Add the elements of a list (or any iterable), to the end of the current list|
|.index()|    Returns the index of the first element with the specified value|
|.insert()|    Adds an element at the specified position|
|.pop()|        Removes and returns the element at the specified position; if no index is specified, removes and returns last element of the list.|
|.remove()|    Removes the first item with the specified value|
|.reverse()|    Reverses the order of the list|
|.sort()|        Sorts the list|

Used in practice:

```
>>> my_list.append("cool beans")
>>> my_list
['Hello', 'world', 'cool beans']
>>>my_list.pop()
'cool beans'
>>> my_list
>>> ['Hello', 'world']
```



The main difference between tuples and lists is that lists are mutable, which means that you can add or delete items to a list once it is created. Tuples are unmutable and cannot be changed once created. This fact can be utilized to sometimes improve performance, typically if you are storing the same value as different variables as they will then point to a single memory address instead of one each which would be the case for lists.  


#### Dictionaries
Dictionaries are unordered collections of data in key:value pairs. Curly brackets are used to define dictionaries:

```
thisdict =    {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
x = thisdict["model"]
print(x)
Mustang 
```

It's also possible and useful to create dictionaries with lists in them or lists of lists. Some examples:

```
>>> schedule = {}
>>> schedule['Rickard'] = ['Monday', 'Tuesday', 'Friday']
>>> schedule['Gwenna'] = ['Tuesday', 'Wednesday', 'Thursday','Friday']
>>> schedule['Pedro'] = ['Wednesday', 'Thursday', 'Friday']
>>> schedule
>>> {'Rickard': ['Monday', 'Tuesday', 'Friday'], 'Gwenna': ['Tuesday', 'Wednesday', 'Thursday', 'Friday'], 'Pedro': ['Wednesday', 'Thursday', 'Friday']}
```
If we then want to access the items:

```
 schedule['Gwenna']
['Tuesday', 'Wednesday', 'Thursday', 'Friday']
```
Since it is a list we can use methods that work on lists on that expression:

```
>>> schedule['Gwenna'][0]
'Tuesday'
>>> schedule['Gwenna'][-1]
'Friday'
>>> len(schedule['Gwenna'])
4
``` 
`len()` returns the length of the provided object (string, list, dict etc.).

Dictionaries have several inbuilt methods. Some of these are:

|Method | Description|
---|---
.keys() | returns a list  all the keys
.items() | returns a list  all the items
.pop() | Removes and returns an element from a dictionary having the given key


### Conditionals
Conditionals are, as you probably are familiar with, fundamental building blocks in programming. Testing whether one condition is true or not is the basic behind conditionals and loops, whether it's "is x true -> then do y" or "for all occurrences of x -> do y".

#### if
The most simple condition in Python, test **if** something is true. If it is true enter the loop and do what is contained within the block. 

*Remember that Python uses white spaces to define blocks of code and new lines.*

```
x = 10
y = 200
if x > y:
  print("x is bigger than y")
```

#### elif
elif is the pythonic way of saying "if the previous conditions were not true, then try this condition".

```
x = 10
y = 200
if x > y:
	print("x is bigger than y")
elif x == y:
	print ("x is equal to y")

```

### else
An Else block is only entered if none of the preceeding blocks were entered (i.e. true):

```
x = 10
y = 200
if x > y:
	print("x is bigger than y")
elif x==y:
	print ("x is equal to y")
else:
	print("x is smaller than y")
```

### for 
The for loop is used for iterating over items in a list, dict, or anything else that can be iterated over,
consider the following example code:

```
x = [1,2,3,4,5,7,8,9,9]

for y in x:
    print(y)
```

Which returns:

```
python test.py
1
2
3
4
5
7
8
9
9
```

#### While 
Execution stays within a block **while** the condition is true. Keep in mind that this can lead to the program becoming stuck in an endless loop. 

```
counter = 1
while counter < 5:
    print(counter)
    counter+=1
```

#### Opening and writing files
Opening files in Python is done with the `open` function, it takes the file name and a 'mode' as input, depending on whether you want to read (`'r'`) or write(`'w'`)  from/to the file. It creates a **file object** also called a **file handle** (fh). 

```
fh = open("hello.txt", "r") 
```
If you just want to print the contents of the file use:

```
Fh = open(“hello.txt”, “r”) 
print(fh.read()) 
```
And to read a line at a time use `readline`:

```
fh = open("hello.txt", "r") 
print fh.readline() 
```

**In almost all cases you will want to save the contents of the file to a variable so that you can actually work with the file contents**. I.e.

```
fh = open("hello.txt", "r")
contents =  fh.read() ## contents is now a string with all the contents of the file 

```


Writing is then done with `.write()`


```
#Need to open the file for writing
fh = open("output.txt",'w')
fh.write("Stuff you write here get's added to the file")
fh.write("Writing another line")
# Closing the file
fh.close()
```


#### With open - The recommended way of working with files!
The `with open` syntax is generally recommended as you get a clear syntax and files will be automatically closed:

```
with open('output.txt', 'w') as f:  # Use f to refer to the file object
    f.write('Hi there!')
```

In the above code, the **filehandle** (f) is only open during the loop, so there is no risk of leaving a file open. This is usually not a problem for small scripts, but as you write more complex code and are opening and writing to multiple files it could cause a problem.


Something that might be of use to you while doing the exercises below is the `.strip()` method. If invoked on a string it will by default remove white spaces from the beginning and end of strings:

```
>>>some_string = "   hello this is a string    "
>>>some_string.strip()
'Hello this is a string'
## Can be used to remove other characters as well:
another_string = ",,,,,Lorem ipsum dolor sit amet, consectetur adipiscing elit...."
another_string.strip(",.")
'Lorem ipsum dolor sit amet, consectetur adipiscing elit'

```

#### For line in File
A useful syntax that you can use in several of the questions for this lab is the `for line in f` syntax.


``` 
stuff_to_save = []

with open('input.txt', 'r') as f:  # Use f to refer to the file object
    for line in f:  # Line will now be a string containing the contents of each line in the file as you iterate through it
        if line.startswith("Hej"):
            stuff_to_save.append(line)
```
The code above will look through the file `input.txt` and save all lines that begin with "Hej" 
and save them to the list `stuff_to_save`.

### Importing libraries
One of the strengths of Python is the many libraries; some are built-in, others you have to install yourself. These libraries provide great utilities. We will encounter some in these labs but there are too many to even list. If you have a problem in programming chances are quite high that someone else has had the same problem before you and already solved it. Why constantly try to re-invent the wheel? Two of these libraries that you should probably be aware of are `numpy` for handling numbers and `pandas` for data analysis, such as reading files and storing them in more clever formats than Python's built-in ones. An added benefit of these is that they are written in C, and thus are generally orders of magnitude faster than using just base Python. 


How to import a library then? It is rather simple. You just type `import` followed by the name of the library.

#### Quick info on what we expect of your code

You will need to use the scripts you write in this session in some of the following labs, thus make sure that they work as intended!

Your code is expected to run as standalone scripts on the command line. I.e. `python myscript.py` should (maybe with some options) produce the answer to the questions.
It's a great idea to make use of module but you also need to make sure the script actually invokes them!

You are free to write your code in `spyder`, `visual code study` or any other `IDE` if that's what you are comfortable with. Vim or other unix based texteditors are also an option. The important thing is that you test that your code can run in the terminal, so testing it on Uppmax might be a good practise.

#### Question 1:
Run the code below, what happens? What do you think is the purpose behind it and why do you think we want you to read it?

``` 
import this
```
______

### Formating Fasta files
The `.fasta` format is the most common format to handle nucleotide and/or amino acid sequences. It gets its name from the FASTA sequence alignment software, which is now obsolete, but the format lives on. It is a plain text format where the greater-than sign (`>`) indicates the start of the header and the following line(s) in the sequence. It can contain several "header/sequence" lines.

Example protein sequence:

```
>MCHU - Calmodulin - Human, rabbit, bovine, rat, and chicken
ADQLTEEQIAEFKEAFSLFDKDGDGTITTKELGTVMRSLGQNPTEAELQDMINEVDADGNGTID
FPEFLTMMARKMKDTDSEEEIREAFRVFDKDGNGYISAAELRHVMTNLGEKLTDEEVDEMIREA
DIDGDGQVNYEEFVQMMTAK*
```
#### Question 2:
Write a Python program that takes a file that contains a sequence like the one above where the sequence spans over multiple lines ("interleaved fasta file") and convert it into a file where the **sequence** is stored on a single line ("sequential"). 

Output would then look like this:

```
>MCHU - Calmodulin - Human, rabbit, bovine, rat, and chicken
ADQLTEEQIAEFKEAFSLFDKDGDGTITTKELGTVMRSLGQNPTEAELQDMINEVDADGNGTIDFPEFLTMMARKMKDTDSEEEIREAFRVFDKDGNGYISAAELHVMTNLGEKLTDEEVDEMIREADIDGDGQVNYEEFVQMMTAK*
```
Test that your code works on [this file](example_data/C_elegans_NC_001328.1_mt_codingsequences.fna)

You can use [this code skeleton](example_data/code_skeleton_question2.py) to get started. The code skeleton uses `sys.argv` to take input from the commandline. `sys.argv` contains the full command that you used to execute the file. 

```
python code_skeleton_question2.py my_input_file.txt
```
In the script `sys.argv[1]` will then contain the string "my_input_file.txt". 



Tip, it's probably a good idea to look at each line of the input and figure out if it's a header or a sequence line.

You can get input to the script either parsing through the command line thorugh `argparse` or `sys.argv` from the `sys` library [example here](https://www.pythonforbeginners.com/system/python-sys-argv), or interactively using `input()` or any other method that you prefer. 


### Reverse complement
A very common problem that arises when working with sequence files is that sequence information can be encoded on either strand of the DNA molecule. So when the DNA is sequenced it is basically random in which orientation your sequence is. Thus it is important to be able to reverse complement your sequence. 


#### Question 3:

**Write a program that takes a nucleotide fasta file as input and returns a new reverse complemented fasta file as output. It should be able to handle fasta files with more than one entry.**
 You don't need to change the header as in the example code below.

Again make sure that your code works on [this file](example_data/C_elegans_NC_001328.1_mt_codingsequences.fna)


The example below only has one entry to illustrate what **reverse complement** means:

```
>NC_011137.1:5899-7440 Homo sapiens neanderthalensis mitochondrion, complete genome
ATGTTCGCCGACCGTTGACTATTCTCTACAAACCACAAAGACATTGGAACACTATACCTACTATTCGGCGCATGAGCTGGAGTCCTAGGCACAGCTCTAAGCCTCC
```
```
>Reverse complemented
GGAGGCTTAGAGCTGTGCCTAGGACTCCAGCTCATGCGCCGAATAGTAGGTATAGTGTTCCAATGTCTTTGTGGTTTGTAGAGAATAGTCAACGGTCGGCGAACAT
```

### Regular expressions
If you need a reminder about regular expressions from the first lab, they are pattern matching for characters (letters, numbers, signs & whole words). They are very useful for extracting bits of text from larger chunks, or ordering filenames, etc. For example:


`>\w*` 

matches `>NC_011137` in the title string from the fasta example above. `>` is just the character `>`. `\w*` means any "word" character repeating, without the star the match would be only `>N`.

Regular expressions or regex are handled in Python by the built-in `re` library. It can be accessed as such:

```
import re
```

To then actually use it you have to first compile the regex you want to use and then search for it in a string.
Then you use one of the matching options `.findall()`, `.search()` or `.match()`. 
We can use `findall` to count the number of 'PCA' in the PCA article from session 1. `findall` returns a list of all the matches (in this case just 'PCA'):

```
import re

with open('example_data/PCA.txt', 'r') as f:
    text = f.read()

pattern = re.compile(r"PCA")
result = pattern.findall(text)
print("There are {} instances of the word 'PCA' in the wikipedia article about PCA".format(len(result)) )
```
If you run it then it returns:

`There are 167 instances of the word 'PCA' in the Wikipedia article about PCA`
 
Another useful way of doing regex matches is the `.search()` method. It returns a `Match` object which can be used to get out information about the match such as position:

Method | Description
---|---
.span()| returns a tuple containing the start-, and end positions of the match.|
.string() |returns the string passed into the function |
.group() |returns the part of the string where there was a match | 

For example:

```
import re
#Fasta sequence from above
target ="ATGTTCGCCGACCGTTGACTATTCTCTACAAACCACAAAGACATTGGAACACTATACCTACTATTCGGCGCATGAGCTGGAGTCCTAGGCACAGCTCTAAGCCTCC"
pattern = re.compile("TATA")

match = pattern.search(target)

print("The TATA box is between base {} and base {}".format(match.span()[0],match.span()[1]))

```
Which returns:
`The TATA box is between base 52 and base 56`

If you really want to dig down into `re` and regexes in python you can have a look at the [python3 documentation](https://docs.python.org/3/library/re.html). 

Have a look at [this cheatsheet](https://www.debuggex.com/cheatsheet/regex/python). There are many more ways of matching with regexes. 

Before writing code with regexes it's usually a good idea to check that the expression you wrote actually does what you think it does. Have a look at [https://regex101.com/](https://regex101.com/) for a place to test them out. 

#### Question 4:

Write a script that reads the [C\_elegans\_mt.fasta](example_data/C_elegans_mt.fasta) and saves the gene name (eg ATP6) as the key in a **dictionary** with the sequence as the value. 
The script should then print out, with some nice padding text:

 * The number of total sequences in the file.
 * The names of all genes in the file.
 * The name of each gene followed by its length.

 
Submit the script as a separate file along with your answers.

### Code review
The answers you submit to this lab will be reviewed by another student in the class.
All serious businesses/workplaces that involve work with coding should have some form of code review. This is to make sure that the new code that is developed does not cause problems for the company. In addition, it gives feedback to the coder on how they might simplify their code or make it more robust. In order to make this process easier, please comment your code as thoroughly as you feel necessary and try to make it easy to read. 

As a reviewer your job is to assess the following things:

1) Does the code run?

2) Does the code perform the task that was specified in the instructions?

You are free to leave other feedback on other things such as style if the code could be simplified etc.

To make the reviewer's job easier it might be a good idea to leave comments describing the code!

#### What to hand in
Please submit the answers (scripts) to questions 2, 3, and 4.
You don't need to hand in the answer to question 1!
