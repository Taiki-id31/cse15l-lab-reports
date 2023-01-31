# Lab Report 2 - Servers and Bugs (Week 3)  Taiki Yoshino (A17492011)

## Part 1
**#Note**  
The StringServer gets a new string from the URL in the format ```/add-message?s=<string>```, and display it in a new line. For example, as the first picture shows, if you want to display "first_message" on the web page, you can add ```/add-message?s=<string>``` at the end of the URL and replace ```<string>``` as "first_message." Also, the second picture shows that you can add a new message below the first message by iterating the same process.

<img src="lab-report2-image/first_message.png" width="75%">
<img src="lab-report2-image/second_message.png" width="75%">

**#Note**  
The StringServer file consists of two classes: StringServerHandler and StringServer. First, StringServerHandler processes the string information of a URL. As default, this class returns ```output= ""```. And, when you input new string parameters in the format ```/add-message?s=<string>```, ```handleRequest(URI uri)``` method extracts the parameter and adds it at the end of the String sequence of ```output```. Note that if you add or edit the URL in rather than format ```/add-message?s=<string>```, it will not make a any change to the output, but display the error message "404 Not Found!". Second, StringServer contains the main method and has a role in starting to sever using ```StringServerHandler``` class and a user-determined port number. Note that you must input the port number when you execute the code; otherwise, it will return the message "Missing port number! Try any number between 1024 to 49151."
    
```
import java.io.IOException;
import java.net.URI;

class StringServerHandler implements URLHandler {
    String output = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return output;
        } 
        else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    output += parameters[1].toString() + "\n";
                    return String.format(output);
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new StringServerHandler());
    }
}
```

## Part 2  Choose one of the bugs from lab 3.
* **A failure-inducing input for the buggy program, as a JUnit test and any associated code.**
```
  @Test 
  public void testReverseInPlace() {
      int[] input1 = { 1, 2, 3 };
      ArrayExamples.reverseInPlace(input1);
      assertArrayEquals(new int[]{ 3,2,1 }, input1);
  }
```

* **An input that doesn’t induce a failure, as a JUnit test and any associated code**  
 ```
  @Test 
  public void testReverseInPlace() {
      int[] input1 = { 3 };
      ArrayExamples.reverseInPlace(input1);
      assertArrayEquals(new int[]{ 3 }, input1);
  }
``` 
* **The symptom, as the output of running the tests**         
<img src="lab-report2-image/no-symptom.png" width="75%">  
<img src="lab-report2-image/symptom.png" width="75%">  

**#Note**   
When you use ```input1 = {3}``` as an input,```testReverseInPlace``` method returns ```{3}```, which alins with the expected value. On the other hand, when you use ```input1 = {1, 2, 3}``` as an input, the actual returned value is ```{3, 2, 3}```, while the expected value is ```{3, 2, 1}```.
   
   
* **The bug, as the before-and-after code change required to fix it**  

The code before changing.
```
   static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
      }
   }
```  

The code after changing.	
```
  static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length/2; i += 1) {
          int temp = arr[i];
          arr[i] = arr[arr.length - i - 1];
          arr[arr.length - i - 1] = temp;
      }
  }
```               
   
**#Note**  
This bug occurred because ```reverseInPlace``` method uses the input array ```arr``` itself in the process to reverse the sequence. For example, when the method swaps an element, the updated array ```arr``` will still be regarded as the original input array. To avoid this problem, as the code above shows, you can create a new variable ```temp``` to store the element that will be swapped, and make a change at the two indexes in the same iteration.  
	
## Part 3
In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn’t know before.  
**#Note**   
Before week 3 in the lab, I had used JUnit assertions to compare two strings or two integers in CSE12's programming assignments. However, I wondered how to compare double or float data types because these types of data are not determined exactly. My TA informed me that I could use the "assertEquals(double expected, double actual, double delta)" method to resolve this issue. The delta represents the allowable difference between the two values. If the difference between (expected - actual) is less than or equal to delta, the method returns true, otherwise it returns false. I learned that it is important to be careful when setting delta when testing floating-point numbers, as it can lead to bugs.

