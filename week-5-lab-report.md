# Exploring Commands

Commands can be utilized in a variety of ways to achieve interesting and most often useful results. They are like a borderless ocean where there are wonders we are yet to discover. It can be as mind-boggling as a labyrinth or as rewarding as a treasure hunt. Today, we will explore three command-line options for the command ``` grep ``` .

## The ``` -i ``` Option
The ``` grep ``` command is case-sensitive, meaning that it will return lines of the files with words that match your query _EXACTLY_, including the case of each word. Let's try using the ``` grep ``` command **without** the ``` -i ``` option.

``` % grep "september" ./911report/*.txt ```

We are searching through _every single file_ in the 911report file of the word "september". We should expect a massive list of results, right? Here's what we got instead:

``` ./911report/chapter-13.5.txt:                www.september11victims.com/september11Victims); New York Times, Portraits: 9/11/01: ```

Only one pathetic line that doesn't tell us anything. And this is all due to us forgetting the capitalize the "s" in "September". However, everything will change if we add the ``` -i ``` option.

``` 
% grep -i "september" ./911report/*.txt
 
./911report/chapter-9.txt:            On September 11, the nation suffered the largest loss of life-2,973-on its soil as a
./911report/chapter-9.txt:                8:46 A.M. on September 11. At most 2,152 individuals died at the WTC complex who
./911report/chapter-9.txt:            Several factors influenced the evacuation on September 11. It was aided greatly by
./911report/chapter-9.txt:                under one hour on September 11 for most civilians who were not trapped or physically
./911report/chapter-9.txt:            One clear lesson of September 11 is that individual civilians need to take
./911report/chapter-9.txt:                the WTC on September 11.
./911report/chapter-9.txt:            Though almost no one at 9:50 on September 11 was contemplating an imminent total
./911report/chapter-9.txt:                painfully exposed on September 11. To its great credit, the department has made a
./911report/chapter-9.txt:                problems in the command and control of the PAPD also were exposed on September 11, 
```

This is only a snippet of the output, but it already is telling us much more than before! The ``` -i ``` option used here ignores the case of the characters, which is especially useful when we are trying to search for all occurences of a particular term without worrying about typing the correct case for each letter. Below are a few more examples:

``` 
% grep -i "foreword" ./*/*/*.txt    

./government/About_LSC/Comments_on_semiannual.txt:FOREWORD
./government/Gen_Account_Office/InternalControl_ai00021p.txt:Foreword
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:FOREWORD
```
A few of the reports in ./technical/government contains the word "FOREWORD". Using the ``` -i ``` option, it successfully searches all of the occurrences of "FOREWORD" without us having to capitalize the whole word. It surely saves time worrying about capitalization and allows us to quickly searches for the headers of these two reports.


