
# OBJECTIVE
Find the best syntax/BKM to write unit tests for CPP language based programs


# FINDINGS
One shot prompts do not work well for unit tests.
Iterative attempts are better.


# SAMPLE

1. "List all the unit tests that I can write for this in google test format". Then insert the code in the AI Tool, or highlight the code.
It is important to metion what tool you are using for unit test.
For my program I received the following unit test suggestions, which was pretty good.

- Test the API URL Construction:
    ○ Ensure that the URL is correctly constructed with the given API key and zipcode.
    ○ Test with valid and invalid API keys and zipcodes to see if the function handles them correctly.
-  Test the HTTP Request:
    ○ Mock the HTTP request to return a known response and ensure your function parses it correctly.
    ○ Test how your function handles various HTTP errors (e.g., 404 Not Found, 500 Internal Server Error).
-  Test the JSON Parsing:
    ○ Provide a set of JSON responses (both valid and invalid) and verify that your function extracts the temperature correctly.
    ○ Test how your function handles invalid JSON (e.g., missing fields, incorrect data types).
-  Test the Temperature Conversion (if applicable):
    ○ If you're converting temperatures from one unit to another, test that the conversion is accurate.
    ○ Include edge cases such as extremely high or low temperatures.
-  Test Error Handling:
    ○ Ensure that your function throws exceptions or handles errors as expected when given invalid input or when an error occurs during the request or parsing.
-  Test Timeout Handling:
    ○ Simulate a scenario where the API does not respond in a timely manner to test the timeout functionality.
-  Test Main Function:
    ○ Mock the fetch_temperature function to return a fixed value and ensure the main function outputs the expected string.
    ○ Test how the main function handles exceptions thrown by fetch_temperature.

2. Prompt for actual unit test code generation - generate unit test for -insert one of the above bullet points- while also highlighting the function that does it.
This helps the tool understand what are the inputs and outputs to the test properly, and spits out the best output for unit test. 

3. You may also ask the tool to generate descriptive tests for each unit test that it generate.


# NOTES
In general, I experienced that the AI tools are less competent in writing unit tests than generating the code.
It could be because it would not have a wholistic view of the project.
It would suggest a whole lot of changes in the program to make it unit testable, but the actual production code has limitations on doing this.
So lot of manual intervention and decision making are needed to choose unit tests ith good coverage and least interuption to the program design.
What it is good at is, suggesting what unit tests would be required for the file.
Then we would have to point it to the actual class/function for a particular unit test and specifically ask to write unit test for this.





