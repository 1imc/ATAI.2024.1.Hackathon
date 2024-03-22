# OBJECTIVE
Find a good prompt to create a C++ program for making HTTP requests in C++.
I chose to do a program that fetches the temperature of a particular zip code using OpenWeatherMap API.

# FEW USER TEMPLATES THAT WAS TRIED
>> Create a project using OpenWeatherMap to get the temperature of a particular zipcode in cpp.

Copilot gave me a bare minimum code that uses libcurl library and fetches the weather info. It instructed me to install libcurl and also generate a valid API key to provide in the program. It was not production quality code and missed many things.

>> Create a project using OpenWeatherMap to get the temperature of a particular zipcode in cpp with proper error handling, thread safety, and using cpp standard greater than cpp 14.

Copilot gave me an improved code that uses cpr library to make http request, some error conditions were checked(not all), had exceptions handling, included thread safety. Had to compile with cpp17 though since cpr library required it. So, it literally took the greater than cpp14 standard as a condition, and chose a library that had higher cpp standard support. What I meant was, for the program to use moder cpp concepts.

>>create a project using OpenWeatherMap to get the temperature of a particular zipcode in cpp with proper error handling, thread safety, using cpp standards up to cpp 20

Uses the C++ HTTP library cpprestsdk for making HTTP requests. Rest of the conditions asked were applied properly.

>>I want to create a program in cpp with standard upto cpp20. I am trying to create an app using OpenWeatherMap API. Choose a C++ HTTP library for best performance, has active maintenance support and ease of use. The app should take an apikey and zipcode as input and produce the output as temperature in Fahrenheit in that zipcode. Print the output as "Temperature in the pincode <actual pincode> is <temperature in Fahrenheit>. The program should handle all the errors correctly. It should check the validity of each parameter used in a function. It should use modern cpp concepts. It should consider thread-safety, check for timeout, and have good documentation before each function and class. The coding style should be based on CppCoreGuidelines.


# FINAL SYNTAX THAT WORKED BEST
- State the problem in simple language. Example: create a program to get the weather of a particular zipcode
- State language preferance and standards. Example: Use cpp with standards upto 20
- If there are several ways to do this, give criteria you need. Example : Choose a well maintained library that is also easy to use
- Clearly define input of program "Input to the program will be zipcode"
- Clearly define output "Output of the program should be temperature in Fahrenhiet". You can also specify the format of output.
- Specify to validate each parameter in a function before using it.
- Specify the error handling needed.
- Specify exception handling if needed.
- Specify thread safety if applicable.
- Specify documentation you need Example: "Create docstring before each function and class".
- Specify the coding style if any. Example: Use googlecodingstyle or cppcoreguideline.

# NOTES
- Copilot can block the code generated if it matches public code
- IntelGPT organises the code into several files(.h, .cpp, main.cpp) while copilot puts everything into a single cpp file.
- When same question is asked multiple times, it can respond slightly differently. ex: sometimes it used cpr for the above program, other times curl.
- At the end, after the program runs successfully evaluate and iterate by prompting the AI again to make the code perfect.
