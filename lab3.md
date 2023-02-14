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


