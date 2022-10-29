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

```
% grep -i "ahmed al ghamdi" ./*/*.txt

./911report/chapter-1.txt:    In another Logan terminal, Shehhi, joined by Fayez Banihammad, Mohand al Shehri, Ahmed al Ghamdi, and Hamza al Ghamdi, checked in for United Airlines Flight 175, also bound for Los Angeles. A couple of Shehhi's colleagues were obviously unused to travel; according to the United ticket agent, they had trouble understanding the standard security questions, and she had to go over them slowly until they gave the routine, reassuring answers.
./911report/chapter-1.txt:    Shehhi and his team, none of whom had been selected by CAPPS, boarded United 175 between 7:23 and 7:28 (Banihammad in 2A, Shehri in 2B, Shehhi in 6C, Hamza al Ghamdi in 9C, and Ahmed al Ghamdi in 9D). Their aircraft pushed back from the gate just before 8:00.
./911report/chapter-13.4.txt:            Dates of U.S. visas obtained in 2000: Ahmed al Ghamdi (September 3), Saeed al Ghamdi
./911report/chapter-13.5.txt:                Ahmed al Ghamdi, one of the earliest operatives to transit Dubai, acquire a mobile
./911report/chapter-13.5.txt:            The next set, Ahmed al Ghamdi (Flight 175) and Moqed (Flight 77), arrived at Dulles
./911report/chapter-13.5.txt:                Hanjour, Majed Moqed, Nawaf al Hazmi, Hamza al Ghamdi, Ahmed al Ghamdi, Saeed al
./911report/chapter-7.txt:                to Connecticut. There he says he found them with new roommates-Ahmed al Ghamdi and
./911report/chapter-7.txt:                Hanjour, Moqed, probably Ahmed al Ghamdi, and Abdul Aziz al Omari; Hazmi's old
./911report/chapter-7.txt:                Omari, Ahmed al Ghamdi, Hamza al Ghamdi, Mohand al Shehri, Majed Moqed, Salem al
./911report/chapter-7.txt:            Four of them-Ahmed al Ghamdi, Saeed al Ghamdi, Hamza al Ghamdi, and Ahmad al
./911report/chapter-7.txt:                instance, although Ahmed al Ghamdi, Hamza al Ghamdi, and Saeed al Ghamdi attended
./911report/chapter-7.txt:                Chechnya. Only two-Ahmed al Ghamdi and Saeed al Ghamdi-had documentation suggesting
./911report/chapter-7.txt:                martyr and whom he asked to recruit a friend, Ahmed al Ghamdi, to the same cause.
./911report/chapter-7.txt:                Ghamdi, flew from Iran to Kuwait. In November, Ahmed al Ghamdi apparently flew to
./911report/chapter-7.txt:                Hazmi. Two days later, Ahmed al Ghamdi and Abdul Aziz al Omari, who had been living
```

In this example, I use the ``` -i ``` option to search for the occurrence of a name. It is again useful because I don't have to be too careful of mis-capitalizing words, which takes extra time in the process.

## The ``` -o ``` Option
The ``` -o ``` option displays _only_ the word that you are searching instead of the whole line when you use the command regularly. This is useful when you are just trying to grasp a general idea of how often a word appears in a particular file. It saves space, which makes the output more legible. Let's look at an example:

``` 
% grep -o "CAPPS" */*.txt

911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-1.txt:CAPPS
911report/chapter-11.txt:CAPPS
911report/chapter-12.txt:CAPPS
911report/chapter-12.txt:CAPPS
911report/chapter-12.txt:CAPPS
911report/chapter-12.txt:CAPPS
911report/chapter-13.2.txt:CAPPS
911report/chapter-13.2.txt:CAPPS
911report/chapter-13.2.txt:CAPPS
911report/chapter-13.3.txt:CAPPS
911report/chapter-3.txt:CAPPS
911report/chapter-3.txt:CAPPS
```
Here, I am trying to see how often the term "CAPPS" appear in the files. If I didn't use the ``` -o ``` option, I would be given a huge glob of lines. It would be pretty unreadable. With the ``` -o ``` option, I can easily tell how often "CAPPS" appears in each chapter. Here, I can see that "CAPPS" is mentioned especially frequently in Chapter 1 of the 911report, but is barely talked about in Chapter 3.

Let's look at another example:

``` 
 % grep -o "D.C." */Media/*.txt

government/Media/A_Perk_of_Age.txt:D.C.
government/Media/Aid_Gets_7_Million.txt:DeCo
government/Media/Avoids_Budget_Cut.txt:D.C.
government/Media/Avoids_Budget_Cut.txt:D.C.
government/Media/Free_legal_service.txt:D.C.
government/Media/Good_guys_reward.txt:D.C.
government/Media/Greedy_Generous.txt:D.C.
government/Media/Greedy_Generous.txt:D.C.
government/Media/Law-school_grads.txt:D.C.
government/Media/Legal-aid_chief.txt:D.C.
government/Media/Marylands_Legal_Aid.txt:D.C.
government/Media/New_Online_Resources.txt:D.C.
government/Media/Texas_Lawyer.txt:D CA
government/Media/Texas_Lawyer.txt:D.C.
government/Media/The_Columbian.txt:D.C.
government/Media/The_State_of_Pro_Bono.txt:D.C.
government/Media/The_State_of_Pro_Bono.txt:D.C.
government/Media/Using_Tech_Tools.txt:D.C.
government/Media/Using_Tech_Tools.txt:D.C.
government/Media/man_on_national_team.txt:D.C.
government/Media/man_on_national_team.txt:D.C.
```

I used ``` grep -o ``` to search for the word "D.C." from technical/government/Media here. It is returning me all the files that contain the word "D.C." without actually returning me the passage. We can use this to gauge how often or not often the government is mentioned in certain media articles.

```
 % grep -o "men" */Alcohol_Problems/*.txt 

government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
government/Alcohol_Problems/DraftRecom-PDF.txt:men
```

I searched the word "men" in the files of technical/government/Alcohol_Problems here. This is only a snippet of the code as "men" is mentione _very often_. We can use it to compare to the output if I had searched "women".

```
% grep -o "women" */Alcohol_Problems/*.txt

government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
government/Alcohol_Problems/Session2-PDF.txt:women
```
We can see here that "men" are mentioned more often than "women" in the folder addressing alcohol problems. We can maybe deduce that men are more likely to have alcoholic issues than women. Or, we can claim that the articles have a bias against men. Here, the ``` -o ``` option is useful when we are comparing the frequency of the appearances of different words, whether to discover different social phenomena, or, just for fun!

```
% grep -o "gene" biomed/*.txt

biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
biomed/gb-2003-4-6-r39.txt:gene
```

I searched for the word "gene" in the biomed folder. I was returned several clean lines of output instead of an enormous amount of text. It would be useful if I am searching for research done specifically on genetics.

## The ``` -n ``` Option
This option, additional to returning you the file names and the lines containing the query, returns you the _line number_ where the word appears. Let's take a look at a few examples to see how it can be used.

```
% grep -n "Bin Laden" */*.txt

911report/chapter-11.txt:161:                terrorist leader, with the headline "U.S. Hard Put to Find Proof Bin Laden Directed
911report/chapter-13.3.txt:36:                www.npr.org/display_pages/features/feature_1253796.html). 14. "Bin Laden's 'Letter
911report/chapter-13.3.txt:278:                Fleecing Bin Laden," Wall Street Journal, Dec. 3, 2001, p. A1.
911report/chapter-13.3.txt:392:            87. For general information on Hage, see Oriana Gill, "Hunting Bin Laden: A Portrait
911report/chapter-13.3.txt:428:            93. ABC News interview, "Terror Suspect: An Interview with Osama Bin Laden," Dec. 22,
911report/chapter-13.3.txt:467:                Statements of Prosecutor and Judge, United States v. Bin Laden, No. S(7) 98 Cr. 1023
911report/chapter-13.3.txt:1060:                FBI Special Agent Daniel Coleman, United States v. Usama Bin Laden, No. S(7) 98 Cr.
```
Let's say I want to learn more about Bin Laden when I am researching on the 911 tragedy. I can use the ``` -n ``` option to search for his name, which will return me which lines of the files he appears in. It is useful as that way I can go directly to those lines to read something more specific about him.

```
% grep -n "circadian rhythms" */*.txt

biomed/1471-213X-1-9.txt:12:        analysis of circadian rhythms in 
biomed/1471-2202-3-1.txt:20:        neural and behavioral substrates of circadian rhythms
biomed/1471-2202-3-1.txt:47:        examples of circadian rhythms, which are typically analyzed
biomed/1471-2202-3-1.txt:664:          evaluate circadian rhythms data [see [ 44 ] ]). The area
biomed/1471-2202-3-1.txt:1188:          Drosophila circadian rhythms data,
biomed/1471-2202-3-20.txt:19:        lack circadian rhythms after lesioning of the SCN [ 6 7 8 9
biomed/1471-2202-3-20.txt:20:        ] , suggesting that circadian rhythms and sleep homeostasis
biomed/1471-2202-3-20.txt:59:        In both flies and mammals, circadian rhythms are thought
biomed/1471-2202-3-20.txt:402:        circadian rhythms.
biomed/1471-2202-3-5.txt:81:        analysis of circadian rhythms [ 27 ] . Here we apply two
biomed/1471-244X-3-5.txt:269:        that regulates circadian rhythms responsible for many
biomed/1471-244X-3-5.txt:328:        circadian rhythms that are correctable by light therapy [
biomed/gb-2001-2-3-research0008.txt:23:        drive circadian rhythms in locomoter activity [ 16, 17].
plos/journal.pbio.0020013.txt:12:        long-term memory, circadian rhythms, immune response, and biogenesis of organelles
```
Imagine that you are doing research on the circadian rhythm of humans. And you remember reading about its relations with other biological responses in our body. You can use the ``` -n ``` option to see which line it appears with the other biological phenomenon you have in your mind. You can then go straight to that line listed. Isn't that useful?

```