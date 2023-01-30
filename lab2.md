# Lab Report 2 - Servers and Bugs (Week 3)  Taiki Yoshino (A17492011)

## Part 1
**#Note**  
The web server StringServer will get a new string and desplay it in a new line. For example, as the two pictures shows, if you want to display "first_message" on the web page, you can add /add-message?s=<string> at the end of the URL, replacing <string> as "first_message". Also, you can add another message by iterating the same process or changing the message.

<img src="lab-report2-image/first_message.png" width="75%">
<img src="lab-report2-image/second_message.png" width="75%">

**#Note**  
This is the code of StringServer, which consists of two classes: StringServerHandler and StringServer.  
  
Firstly, StringServerHandler is the class to processes the information of the URL. As the default, this class returns (output= ""), and when you added /add-message?s, then the string parameters will be added to the output and it will be displayed. Note that if you add somethig rather that /add-message?s, then it will cause an error.
  
Secondly, StringServer is the class contains main method and start sever using StringServerHandler class and port number. Note that this class requires an input of port number.
    
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

## Part 2  
* A failure-inducing input for the buggy program, as a JUnit test and any associated code.
```
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = { 1, 2, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3,2,1 }, input1);
	}
```

* An input that doesn’t induce a failure, as a JUnit test and any associated code 
 ```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
``` 
* The symptom, as the output of running the tests
  
  
* The bug, as the before-and-after code change required to fix it 
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

## Part 3
**#Note**   

