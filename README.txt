Test Report

Using the service

● Prerequisite
	Install and run Docker.
● Running the service
	docker run -p 8080:8080 -it casumo/devowelizer:latest
● Service API
	GET /:input should return the input without the vowels.

During the testing of GET /:input service,  11 diferent cases are covered, 17 tests are written and executed. Testing tool used for this process was Postmaan.

Test cases:

1. Input with mixed vovels and consonants
Input: "input"
Expected Result: Status Code 200, "ipt"
Status: Works as expected

2. Input with only consonants
Input: "xyz"
Expected Result: Status Code 200, "xyz"
Status: Works as expected

3. Input with only vowels
Input: "aeiou"
Expected Result: Status Code 200, ""
Status: Works as expected

4.1. Input with uppercase and lowercase letters
Input: "PostmAn"
Expected Result: Status Code 200, "Pstmn"
Status: Failed - uppercase letters are not recognised as vowels, and havent been remowed.
Actual result: Status Code 200, "PstmAn"

4.2.
Input: "HeLLo WoRLd hEllO wOrld"
Expected Result: Status Code 200, "HLL WRLd hll wrld"
Status: Failed - uppercase letters are not recognised as vowels, and havent been remowed.
Actual result: Status Code 200, "HLL WRLd hEllO wOrld"

5. Input a lage number of characters
Input: 520 alphabetical characters
Expected Result: Status Code 200, vowels are removed
Status: Works as expected

6. Only numerical input
Input: "12345"
Expected Result: Status Code 200, "12345"
Status: Works as expected

7. Empty input
Input: ""
Expected Result: Status Code 200,  Empty String
Status: Failed - if the message that is returned is expected, it must be more accurate, and with diferent status code.
Actual result: Status Code 200, "Send GET to /:input"

8. Input space
Input: " "
Expected Result: Status Code 200, " "
Status: Works as expected

9. Input non-English characters
Input: "лишће, lišće"
Expected Result: Status Code 200, "лшћ, lšć"
Status: Failed - service does not differ cyrillic vowels and consonants.
Actual result: Status Code 200, "лишће, lšć"

10 Input special characters
Input: "a+b"
Expected Result: Status Code 200, "+b"
Status: Works as expected

11.1. Input special characters URL encoding
Input: "input=c%2B%2B%20programming"
Expected Result: Status Code 200, "npt=c++ prgrmmng"
Status: Works as expected

11.2.
Input:"Innppoot%64m%65m"
Expected Result: Status Code 200, "Innppootdmm"
Status: Works as expected

11.3.
Input: "%D1%87%D0%B0%D1%98"
Expected Result: Status Code 200, "чј"
Status: Failed - service does not differ cyrillic vowels and consonants.
Actual result: Status Code 200, "чај"
11.4.
Input: "%20"
Expected Result: Status Code 200, " "
Status: Works as expected

11.5.
Input: "%23hashtag"
Expected Result: Status Code 200, "#hshtg"
Status: Works as expected

11.6.
Input: "/%21%40%23%24%25%5E%26%2A%28%29_%2B-%3D%5B%5D%7B%7D%7C%3B%27%3A%22%2C.%2F%3C%3E%3F"
Expected Result: Status Code 200, "!@#$%^&*()_+-=[]{}|;':",./<>?"
Status: Works as expected

**Collection and test results are provided along with this report

Additional info:

With manual execution of single test multiple time over and over again, each 5th time servis will return Internal server error, code 500. Doker logs does't provide any info.
When whole colection is launched in a few iterations, than error 500 does not occur exclusively on every 5th execution.
Another issue is about performance - service could be fast considering its simplicity (curently it is between 2 and 5 seconds)

There are several measures that can be implemented to consistently safeguard and monitor the reliability of the Devowelizer service:
1. Automated testing: Write automated tests that cover all of the functionality of the service, including edge cases and error handling. Run these tests regularly to ensure that any changes or updates to the service do not introduce new bugs. Automated tests can be run as part of a continuous integration/continuous deployment (CI/CD) pipeline to catch any issues early on in the development process.
2. Monitoring: Set up monitoring tools to track the performance and availability of the Devowelizer service. Monitoring can also help to identify any patterns or trends in service usage that can help to optimize the service for better performance.
3. Error handling: Implement robust error handling in the Devowelizer service to ensure that it fails gracefully in the event of unexpected input or other errors. This can prevent the service from crashing or behaving unpredictably, which can negatively impact the reliability of the service.
4. Logging: Implement logging to track the behavior of the Devowelizer service and capture any errors or issues that arise. This can help to identify the root cause of any problems that arise and take appropriate action to address them.
5. Scalability: As the usage of the Devowelizer service grows, it may need to scale the service to handle the increased traffic. Mesures can be implemented such as load balancing and auto-scaling to ensure that the service can handle increased traffic without compromising its reliability.