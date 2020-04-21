# [Steps of fuzzing a web application](https://medium.com/swlh/fuzzing-web-applications-e786ca4c4bb6)

**1. Determine the data entry points**
- Identify ways a client can provide input to the application.
- What are the endpoints that take input? 
- What are the parameters used? 
- What headers do the application use?

**2. Decide on the payload list**
Determine what data to feed to the application. 
For web applications, the most useful fuzzing data would be lists of known XSS payloads, SQLi payloads, and so on. 

Recommended [SecLists](https://github.com/danielmiessler/SecLists/tree/master/Fuzzing) for a pretty comprehensive payload list for fuzzing web applications.
SecList is pretty good for detecting already known vulnerabilities. Another way of fuzzing is to generate payloads randomly, including payloads like the below to try to induce errors in the web app:

-   Payloads that are really long,
-   payloads that contain odd characters of various encodings,
-   and payloads that contain certain special characters, like the new line character, the line feed character, and more.

By feeding the application garbage data like this, you might be able to detect unexpected behavior and discover new classes of vulnerabilities!

**3. Fuzz**
Now, all there is to do is to systematically feed your fuzz payload list to the data entry points of the application! There are several ways of doing it, depending on your needs and your programming skills.

**4. Monitor the results**
Analyze the results your fuzzer returned. 
Look for patterns and anomalies from the server response. What you should be looking for will depend on the payload set that you use.
For example, when fuzzing for SQLi, you might want to look for a change in content length or response time.
And when searching for path traversals, you might look for special keywords in the response.
Looking more into each vulnerability type will help you identify the key signatures of each vulnerability being present.
