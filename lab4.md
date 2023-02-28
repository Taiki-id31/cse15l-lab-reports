# Lab Report 4 - (Week 7)  Taiki Yoshino (A17492011)

## Step4: Log into ieng6   
Entered command   
```$ssh <Ctrl-R> c <Return>``` 

Executed Command  
```$ssh cs15lwi23aht@ieng6.ucsd.edu``` 


## Step5: Clone your fork of the repository from your Github account 
Entered command   
```$git clone <Command-V> ``` 

Executed Command  
```$git clone https://github.com/Taiki-id31/lab7.git```


## Step6: Run the tests, demonstrating that they fail
Entered & Executed command   
```$cd lab7 ``` 

Entered command    
```$<Ctrl-R> javac <Return> ``` 

Executed Command      
```$javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java```

Entered command      
```$<Ctrl-R> java <up> <up> <Return> ``` 

Executed Command     
```$java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests```


Entered command     
```$git clone <Command-V>```

Executed Command      
```$git clone https://github.com/Taiki-id31/lab7.git```


## Step7: Edit the code file to fix the failing test
Entered and Executed command   
```$nano  ListExamples.java```    

Edit the file.   

```<Ctrl-O> <Return> <Ctrl-X>``` 

## Step8: Run the tests, demonstrating that they now succeed
Entered command  
```$<Ctrl-R> javac <Return>``` 

Executed Command       
```$javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java```


Entered command  
```$<Ctrl-R> java <up><up><up><up><up><up><up><up><Return>``` 

Executed Command    
```$java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests```


## Step9: Commit and push the resulting change to your Github account (you can pick any commit message!)
Entered command  
```$git add <tab> <Ctrl-V> <return>```   

Executed Command   
```$git add ListExamples.java ```

Entered and Executed command 
```$git commit -m "commit"```   


Entered and Executed command  
```$git push``` 







**Description**  
```grep -r``` is an option to find all files that contain specified strings from the current directory and its sub-directory. The default ```grep``` command checks only one specified file, so you have to visit every file, but ```grep -r```allows you to search files recursively. The Ex1-1's command outputs the file names and sentences, which include "Lucayans" from all sub-directories in ```./written_2```. You can also specify two strings to search, as Ex1-2 shows. This command searches files that contain 'seafood' or 'Japan.'
  

  
Output  
```
travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

**Ex1-2**   
Command   
```$ grep -r 'seafood\|Japan'``` 
   
Output  
```
non-fiction/OUP/Abernathy/ch15.txt:As we pointed out in Chapter 13, regionalization of apparel production in three main areas has started to occur. In the U.S. market, most sewing operations take place in Mexico and the Caribbean Basin; in Europe, sewing operations go to North Africa, Turkey, and Eastern Europe; and in Japan, sewing operations go to various East Asian regions. The formal analysis in Chapter 7 specified the factors that determine whether production of items under rapid replenishment policies should be done domestically or outsourced to low wage countries.
non-fiction/OUP/Abernathy/ch15.txt:For textiles, with their high capital costs, lower labor content, and emphasis on high quality and finishing operations, the concentration in the southeastern United States, Korea and Japan, and industrial Europe may be expected largely to continue. But the longer term viability of American textile centers will depend on the development of infrastructures capable of supporting advanced textile production in countries close to the U.S. market, such as Mexico and elsewhere in Latin America.
...
```


## Option2: Display file names which file matches specified patterns using ```grep -l``` 
**Description**  
```grep -l``` is an option to display only the file names which match specified patterns. If you want to know only the filenames of the output of Ex1-1 and Ex1-2, you can use ```-l``` like the Ex2-1 and Ex2-2. Note that Ex2-1's output is only one file while there are two outputs in Ex1-1. This is because 'Lucayans' appears two times in Bahamas-History.txt. Therefore, ```-l``` option is helpful when you want to know how many files have 'Lucayans' excluding duplicates.

**Ex2-1**    
Command   
```$ grep -l -r 'Lucayans'``` 

Output  
```
travel_guides/berlitz2/Bahamas-History.txt
```

**Ex2-2**   
Command   
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
```grep -c```is an option to count how many lines match the given pattern or string. Ex3-1 command demonstrates how many times "Lucayans" appears in the ```travel_guides/berlitz2/Bahamas-History.txt```, and its output supports the previous reasoning that there are two "Lucayans" in the same files. You can also search the strings in each file recursively using ```-r``` as Ex3-2 shows.

**Ex3-1**      
Command   
```$ grep -c "Lucayans" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
2
```

**Ex3-2**     
Command   
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
```grep -i```is an option to search the matching lines case-insensitively. For example, "the" and "The" are regarded as the same. Ex4-1 shows that if you consider the case regarding "cuba," there are no matches, but if you don't care about the case, there are five matches. Likewise, the matches regarding 'The" increases if you do search case-insensitvely.

**Ex4-1**    
Command   
```$ grep -c "cuba" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
0
```

Command   
```$ grep -c -i "cuba" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
5
```

**Ex4-2**   
Command   
```$ grep -c "the" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
30
```

Command   
```$ grep -c -i "the" travel_guides/berlitz2/Bahamas-History.txt``` 

Output  
```
32
```


## References 
I referred to the following site about the four grep options and their usages.  
[https://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/](https://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/)
