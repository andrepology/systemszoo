+ A bug is a test case you haven't written yet

-   Designing test cases that are specific, automated, and independent
	- In a separate module, create tests that inherit from `unittest`. 
		- class TestCuboid(unittest.TestCase)
		- methods starting with `test_`
-   Writing test cases _before_ the code they are testing
	- #pattern: writing an empty function with docstrings rather than stubs (!) 
-   Writing tests that test good input and check for **proper** results
-   Writing tests that test bad input and check for **proper failure responses**
-   Writing and **updating test cases to reflect new requirements**
- Refactoring mercilessly to improve performance, scalability, readability, maintainability, or whatever other -ility you’re lacking