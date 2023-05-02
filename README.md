Download Link: https://assignmentchef.com/product/solved-cmpt141-assignment5-dictionaries-and-file-i-o
<br>
<h1></h1>

Cities are highly complex systems, yet we rarely think about them that way. They produce and have access to lots of <strong>data</strong>! The City of Saskatoon even has an Open Data Catalogue (<em>http://opendata-saskatoon.cloudapp.net/</em>) which anyone can access. In this assignment, we are going to use Python to build a program that parses some of this data, and analyzes it at the neighbourhood level.

Saskatoon uses as ward system in its civic election system. Meaning that Saskatoon is divided evenly into several <strong>wards</strong>. And each ward is divided into several <strong>neighbourhoods</strong>. In this assignemnt, we will be looking specifically at data that tells us which languages are spoken in each neighbourhood.

This assignment is divided into 5 different “questions”, but in the end, your work from all of the questions will be combined to complete the overall program. The first four questions will each ask you to define a function that will perform a specific task. Make sure that the inputs (parameters) and outputs (return values) of your functions match the problem description <strong>exactly</strong>, or else the whole thing won’t fit together properly!

The following is a brief overview of how the questions for this assignment will fit together:

<ul>

 <li><strong>Question 1</strong>: Read data about the city from a text file and organize it as a <strong>database</strong>. <strong>You must fully complete this question before moving on.</strong></li>

</ul>

All of the other questions will depend on the database that you create here.

<ul>

 <li><strong>Question 2</strong>: Build a list of all the <strong>unique </strong><em>wards </em>in the city.</li>

 <li><strong>Question 3</strong>: Build a list of all the <em>neighbourhoods </em>in a given ward.</li>

 <li><strong>Question 4</strong>: Count how many times each <em>language </em>occurs within a given list of neighbourhoods.</li>

 <li><strong>Question 5</strong>: For each <em>ward</em>, display the <em>neighbourhood language </em></li>

</ul>

Individually, none of these questions are particularly difficult, but if you make a mistake anywhere along the way, then the last part won’t work. Make sure to perform simple testing, such as printing out lists or dictionaries, as you go to make sure that everything looks right.

<strong>One last note of caution: </strong>We have given you an input file for this assignment. Be aware that we will test your program with a different input file, that contains <strong>different </strong>neighbourhood data. Therefore, you must make sure your code is fully general; don’t count on knowing exactly how many neighbourhoods/wards there are, or on knowing exactly what languages there might be.!

<strong>Question 1</strong>

<strong>Purpose: </strong>To practice the concept of dictionary as a database

<strong>Degree of Difficulty: </strong>Moderate.

Before starting this question, first, download the data file CityData.txt from the class Moodle. Make sure to put it in the same folder as your a5.py python code.

Write a function called read_citydata() that takes as parameter(s):

<ul>

 <li>a string indicating the name of a city data file</li>

</ul>

This function should <strong>return </strong>a database (i.e. a dictionary-of-dictionaries) that stores all of the City data in a format that we will describe further below. You can review section 11.1.9 of the text for a refresher on what databases look like using dictionaries.

<h2>Input File Format</h2>

The data file for this question looks like this:

Holiday Park,Ward 2,Spanish,English,French,Ukrainian,Cree,German

North Park,Ward 1,Tagalog,Ukrainian,French,German,English

Each line of the file contains all of the data for a single neighbourhood. The first item on the line is always the neighbourhood’s name; names are guaranteed to be unique. The second item is always the neighbourhood’s ward, which in the example above, is Ward 2. Following that are <strong>one or more </strong>languages which are spoken in that neighbourhood. So there are residents in Holiday Park that speak Spanish, English, French, Ukrainian, Cree, or German. Note that the language names CAN contain spaces. All of the data items on a each line are separated by commas.

<h2>Database Format</h2>

Your function should open the file given as a parameter and read the data from it into a database. The keys for this database will be neighbourhood names, and the values will be records (i.e another dictionary) for the matching neighbourhood.

First, the read_citydata() function should create an empty dictionary to be the overall database.

Then, for each neighbourhood from the input file, create one record (i.e. one dictionary) with the following fields:

<ul>

 <li>The neighbourhood’s name, as a string.</li>

 <li>The ward, as a string.</li>

 <li>The spoken languages, as a <strong>list </strong>of strings.</li>

</ul>

This record should then be added to the database, using the neighbourhood’s name as a key.

Once all of the records have been added, the function should return the database dictionary.




<strong>Question 2 </strong>

<strong>Purpose: </strong>To practice iterating over data

<strong>Degree of Difficulty: </strong>Easy.

Write a function called find_wards() which takes as parameter(s):

<ul>

 <li>A dictionary in the format of the city database as described in Q1</li>

</ul>

This function should construct and <strong>return </strong>a <strong>list </strong>of all the different wards. Each entry in the list should be unique; in other words, don’t add the same ward twice. For the input file you were given, the resulting list




should be (though not necessarily in this order):

[’Ward 1’, ’Ward 9’, ’Ward 5’, ’Ward 2’, ’Ward 3’,

<table>

 <tbody>

  <tr>

   <td> </td>

  </tr>

 </tbody>

</table>

’Ward 4’, ’Ward 6’, ’Ward 8’, ’Ward 7’, ’Ward 10’]

Also, note that this function <strong>must not change </strong>the city database in any way.

<strong>Question 3</strong>

<strong>Purpose: </strong>To practice iterating over nested compound data and accessing different dictionary fields

<strong>Degree of Difficulty: </strong>Easy.

Write a function called ward_neighbourhoods() which takes as parameter(s):

<ul>

 <li>A dictionary in the format of the city database as described in Q1</li>

 <li>The name of a ward, as a string</li>

</ul>

The function should construct and <strong>return </strong>a <strong>list </strong>containing the <strong>neighbourhoods </strong>that can be found in a particular ward. For example, for the input file you were given, if the ward is “Ward 2”, the resulting list




should be (though not necessarily in this order):

[’Meadowgreen’, ’Westmount’, ’Pleasant Hill’, ’Caswell Hill’,

<table>

 <tbody>

  <tr>

   <td> </td>

  </tr>

 </tbody>

</table>

’Montgomery Place’, ’King George’, ’Holiday Park’, ’Riversdale’]

Also, note that this function <strong>must not change </strong>the city database in any way.

<strong>Question 4 </strong>

<strong>Purpose: </strong>To practice summarizing data from a dictionary

<strong>Degree of Difficulty: </strong>Moderate.

Write a function called count_languages() which takes as parameter(s):

<ul>

 <li>A dictionary in the format of the city database as described in Q1</li>

 <li>A list of neighbourhood names (as strings)</li>

</ul>

This function should construct and <strong>return </strong>a <strong>dictionary </strong>where each key is a <strong>language </strong>(e.g. English or French, etc…) and the value for that key is the number of neighbourhoods of that speak that language in a given list. For example, using the sample list of all of the neighbourhoods from “Ward 2” (see Q3 to see that list), the

resulting dictionary should be:

{’Sino-Tibetan languages’: 2, ’Chinese’: 1, ’Mandarin’: 1, ’Arabic’: 1,

’Bengali’: 1, ’French’: 5, ’English’: 8, ’German’: 4, ’Cree’: 6, ’Tagalog’: 4,

<table>

 <tbody>

  <tr>

   <td> </td>

  </tr>

 </tbody>

</table>

’Ukrainian’: 5, ’Spanish’: 2, ’Cantonese’: 1}

Also, note that this function <strong>must not change </strong>the city database or the given list of neighbourhood names in any way.

<strong>Evaluation</strong>

<ul>

 <li><strong>-1 mark </strong>for lack of identification in the solution.</li>

 <li>1 mark: The function parameters and return value are the correct data type</li>

 <li>1 mark: The format of the returned dictionary is correct</li>

 <li>1 mark: The counts are correctly calculated</li>

 <li>1 mark: For a good function docstring</li>

</ul>




<strong>Question 5 </strong>

<strong>Purpose: </strong>To practice solving a problem by calling multiple functions; to practice passing data results between functions

<strong>Degree of Difficulty: </strong>Easy if you did everything right so far

Now it’s time to put all your functions together to print out a summary report of the number of neighbourhoods that speak unique languages in each ward.

In the main part of your program, write code that will <strong>print to the console </strong>the name of each ward, the TOTAL number of different neighbourhoods that can be found in that ward, followed by the counts for <strong>number of neighbourhoods </strong>for each spoken language in that ward.

<table width="652">

 <tbody>

  <tr>

   <td width="652">Ward 1 contains 10 neighbourhoods. Below are the languages spoken in the Ward and the number of neighbourhoods where that language is spoken.{’Russian’: 1, ’Telugu’: 1, ’Hindi’: 1, ’Urdu’: 2, ’Chinese’: 1,’Mandarin’: 1, ’Arabic’: 3, ’German’: 8, ’French’: 8, ’English’: 10,’Bengali’: 1, ’Cree’: 2, ’Tagalog’: 5, ’Punjabi’: 1, ’Gujarati’: 1, ’Ukrainian’: 6}Ward 2 contains 8 neighbourhoods.Below are the languages spoken in the Ward and the number of neighbourhoods where that language is spoken.{’Sino-Tibetan languages’: 2, ’Chinese’: 1, ’Mandarin’: 1, ’Arabic’: 1,’Bengali’: 1, ’French’: 5, ’English’: 8, ’German’: 4, ’Cree’: 6,’Tagalog’: 4, ’Ukrainian’: 5, ’Spanish’: 2, ’Cantonese’: 1}</td>

  </tr>

 </tbody>

</table>

For example, the format for your output might look something like this:

There will be more wards, but we’re only showing two here to save space.

To do this, you will need to make use of all of the functions you have written so far and make good use of their inputs and outputs. If you’ve done everything correctly, this part of your program won’t require a lot of code: just a few function calls and a <strong>single for-loop </strong>should be enough.