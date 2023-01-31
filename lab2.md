# Lab Report 2 - Servers and Bugs (Week 3)  Taiki Yoshino (A17492011)

## Part 1
**#Note**  
The StringServer gets a new string from the URL in the format ```/add-message?s=<string>```, and display it in a new line. For example, as the first picture shows, if you want to display "first_message" on the web page, you can add ```/add-message?s=<string>``` at the end of the URL and replace ```<string>``` as "first_message." Also, the second picture shows that you can add a new message below the first message by iterating the same process.

<img src="lab-report2-image/first_message.png" width="75%">
<img src="lab-report2-image/second_message.png" width="75%">

**#Note**  
The StringServer file consists of two classes: StringServerHandler and StringServer. First, StringServerHandler processes the string information of a URL. As default, this class returns ```output= ""```. And, when you input new string parameters in the format ```/add-message?s=<string>```, ```handleRequest(URI uri)``` method extracts the parameter and adds it at the end of the String sequence of ```output```. Note that if you add or edit the URL in rather than format ```/add-message?s=<string>```, it will display the error message "404 Not Found!". Second, StringServer contains the main method and has a role in starting to sever using ```StringServerHandler``` class and a user-determined port number. Note that you must input the port number when you execute the code; otherwise, it will return the message "Missing port number! Try any number between 1024 to 49151."
    
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
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
      int[] newArray = new int[arr.length];
      for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
      }
      return arr;
  }
```  

The code after changing.	
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length/2; i += 1) {
          int temp = arr[i];
          arr[i] = arr[arr.length - i - 1];
          arr[arr.length - i - 1] = temp;
      }
  }
```               
   
**#Note**  
This bug occurred because the method uses the input array itself in the process to reverse the input. When the method swap an element, the updated array will still be regarded as the original input array. To avoid this problem, we should create a new varible to store the element temporaly, and make a change at two indexes at the same time.  
	
## Part 3
In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn’t know before.  
**#Note**   

