# Lab Report 3 - Researching Commands (Week 5)  Taiki Yoshino (A17492011)

## Option1: Recursive Search using ```grep -r```
**Description**  
```grep -r``` is an option to find all files that contain specified strings from the current directory and its sub-directory. The default ```grep``` command check only one specified file so you have to visit every file, but ```grep -r```allow you to search files recursively.
  
**Example1-1**  
Input   
```$ grep -r "Lucayans"``` 
  
Output  
```
travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

**Example1-2** 
Input   
```$ grep -r 'seafood\|Japan'``` 
   
Output  
```
non-fiction/OUP/Abernathy/ch15.txt:As we pointed out in Chapter 13, regionalization of apparel production in three main areas has started to occur. In the U.S. market, most sewing operations take place in Mexico and the Caribbean Basin; in Europe, sewing operations go to North Africa, Turkey, and Eastern Europe; and in Japan, sewing operations go to various East Asian regions. The formal analysis in Chapter 7 specified the factors that determine whether production of items under rapid replenishment policies should be done domestically or outsourced to low wage countries.
non-fiction/OUP/Abernathy/ch15.txt:For textiles, with their high capital costs, lower labor content, and emphasis on high quality and finishing operations, the concentration in the southeastern United States, Korea and Japan, and industrial Europe may be expected largely to continue. But the longer term viability of American textile centers will depend on the development of infrastructures capable of supporting advanced textile production in countries close to the U.S. market, such as Mexico and elsewhere in Latin America.
...
```


## Option2: Display file names which file matches specified patterns using ```grep -l``` 
**Description**  
```grep -l``` is an option to display only the file names which matches specified patterns. 

**Example2-1**  
Input   
```$ grep -l -r 'Lucayans'``` 

Output  
```
travel_guides/berlitz2/Bahamas-History.txt
```

**Example2-2** 
Input   
```$ grep -l -r 'seafood\|Japan'``` 

Output  
```
non-fiction/OUP/Abernathy/ch15.txt
non-fiction/OUP/Abernathy/ch8.txt
non-fiction/OUP/Abernathy/ch9.txt
...
```

## Option3: Count the number of matches using ```grep -c```
**Description**  
```grep -c```is an option to count how many lines matches the given pattern/string.

**Example3-1**    
Input   
```$ grep -c "Lucayans" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
2
```

**Example3-2**   
Input   
```$ grep -c -r "Lucayans"``` 

Output  
```
non-fiction/OUP/Abernathy/ch1.txt:0
non-fiction/OUP/Abernathy/ch14.txt:0
non-fiction/OUP/Abernathy/ch15.txt:0
...
```

## Option4: Case insensitive search using ```grep -i```  
**Description**   
```grep -i```is an option to search the maching lines case insensitively. For example, "the" and "The" are regarded as the same.

**Example4-1**  
Input   
```$ grep -c "cuba" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
0
```

Input   
```$ grep -c -i "cuba" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
5
```

**Example4-2** 
Input   
```$ grep -c "the" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
30
```

Input   
```$ grep -c -i "the" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
32
```






# Lab Report 3 - Researching Commands (Week 5)  Taiki Yoshino (A17492011)

## Option1: Recursive Search using ```grep -r```
**Description (what it’s doing and why it’s useful.)**  
```grep -r``` is an option to find all files that contain specified strings from the current directory and its sub-directory. The default ```grep``` command check only one specified file, but ```grep -r```can search recursively so you do not have to visit every file.

The StringServer gets a new string from the URL in the format ```/add-message?s=<string>```, and display it in a new line. For example, as the first picture shows, if you want to display "first_message" on the web page, you can add ```/add-message?s=<string>``` at the end of the URL and replace ```<string>``` as "first_message." Also, the second picture shows that you can add a new message below the first message by iterating the same process.

<img src="lab-report2-image/first_message.png" width="75%">
<img src="lab-report2-image/second_message.png" width="75%">

**Note**  
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

## Option2: Count the number of matches using ```grep -c```
**Description (what it’s doing and why it’s useful.)**  
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

**Note**   
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
   
**Note**  
This bug occurred because ```reverseInPlace``` method uses the input array ```arr``` itself in the process to reverse the sequence. For example, when the method swaps an element, the updated array ```arr``` will still be regarded as the original input array. To avoid this problem, as the code above shows, you can create a new variable ```temp``` to store the element that will be swapped, and make a change at the two indexes in the same iteration.  
	
## Option3: Display lines around the matches using ```grep -A,B,C```  
**Description (what it’s doing and why it’s useful.)**   
Before week 3 in the lab, I had used JUnit assertions to compare two strings or two integers in CSE12's programming assignments. However, I wondered how to compare double or float data types because these types of data are not determined exactly. My TA informed me that I could use the ```assertEquals(double expected, double actual, double delta)``` method to resolve this issue. The delta represents the allowable difference between the two values. If the difference between (expected - actual) is less than or equal to delta, the method returns true, otherwise it returns false. I learned that it is important to be careful when setting delta when testing floating-point numbers, as it can lead to bugs.

## Option4: Display file names which file contains specified patterns using ```grep -l``` 
**Description (what it’s doing and why it’s useful.)**  
