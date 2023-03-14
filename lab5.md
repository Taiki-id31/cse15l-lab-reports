# Lab Report 5 - (Week 10)  Taiki Yoshino (A17492011)

## Bash Script in "grade.sh"  
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

cd student-submission
if [[ -f ListExamples.java ]]
then
    echo "ListExamples found"
else
    echo "ListExamples not found"
    exit 1
fi
mkdir lib
cp ../lib/hamcrest-core-1.3.jar ./lib/
cp ../lib/junit-4.13.2.jar ./lib/
cp ../TestListExamples.java ./

javac ListExamples.java

javac -cp $CPATH  TestListExamples.java

if [[ $? -ne 0 ]]
then
    echo "compiler error"
    exit 2
fi

java -cp $CPATH  org.junit.runner.JUnitCore TestListExamples
``` 

## Test1: The same code as the starter from lab3
[https://github.com/ucsd-cse15l-f22/list-methods-lab3](https://github.com/ucsd-cse15l-f22/list-methods-lab3)

Entered command   
```$bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3``` 

Note:  
Since the index2 variable is not properly updated within a for-loop in the ListExamples class, this submission should fail due to a timeout error. The following screenshot indicates that the submitted file was successfully cloned and the ListExamples.java file was found when running the grade.sh script. However, the submission failed due to a timeout exception, as I expected.

Output  
<img src="lab-report5-image/test1.png" width="60%"> 

## Test2: Correct methods (I would expect this to get full or near-to-full credit)
[https://github.com/ucsd-cse15l-f22/list-methods-corrected](https://github.com/ucsd-cse15l-f22/list-methods-corrected)

Entered & Executed command   
```$bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected``` 

Note:  
This submission does not contain any errors in its methods. As a result, I was able to successfully clone the submission, find the specified file, and pass all test cases.

<img src="lab-report5-image/test2.png" width="60%"> 

## Test3: Method including syntax error of a missing semicolon
[https://github.com/ucsd-cse15l-f22/list-methods-compile-error](https://github.com/ucsd-cse15l-f22/list-methods-compile-error)

Entered & Executed command   
```$bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error```     

Note:   
The submitted methods contain some syntax errors, which should cause error during compile time. The following output indicates that I successfully cloned the files, found the specified files, but failed during compilation due to a missing semicolon. It's important to note that the bash script in grade.sh is designed to exit immediately upon encountering a compilation error to prevent the possibility of running a previously compiled file instead of the currently submitted file.

<img src="lab-report5-image/test3.png" width="60%">   

## Test4: The arguments of filter in the wrong order
[https://github.com/ucsd-cse15l-f22/list-methods-signature](https://github.com/ucsd-cse15l-f22/list-methods-signature)

Entered & Executed command   
```$bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-signature```     


Note:   
To test the filter method in the ListExamples class, I created a new test case called testFilter in the TestListExamples class. Since the submitted file's filter method argument is in the wrong order, it should fail during compilation. The picture shows that the submission failed due to a compiler error of incompatible type, as expected.

```
@Test(timeout = 500)
    public void testFilter() {
    List<String> list = Arrays.asList("moon");
    IsMoon ismoon = new IsMoon();
    List<String> filtered = ListExamples.filter(list, ismoon);
    assertEquals(list, filtered);
}
``` 

<img src="lab-report5-image/test4.png" width="60%">  
