# Lab Report 3 - Week 5
##  Grep Matching Line and Line Number: ```-n```
By using ```-n``` with ```grep``` it will return the matching line of the file and before that it will include the line number of the file. This is useful if you want to find the section with a certain word or phrase. For example, you just want to skim through sections of files on a certain topic without reading the whole thing.  
```
# Without Using -n
$ grep "ranges" ./biomed/*.txt
./biomed/1468-6708-3-1.txt:          good, or good health (were 'healthy'). YHL ranges from 0
./biomed/1471-2091-3-31.txt:          Ca 2+; because Ca 2+apparently rearranges the
./biomed/1471-2105-2-8.txt:          ranges of percent identity. The fraction of alignments
./biomed/1471-2105-3-12.txt:            Similarity ranges
./biomed/1471-2105-3-12.txt:            user-defined value. Score ranges are related to the

# Using -n in grep command
$ grep -n "ranges" ./biomed/*.txt
./biomed/1468-6708-3-1.txt:96:          good, or good health (were 'healthy'). YHL ranges from 0
./biomed/1471-2091-3-31.txt:595:          Ca 2+; because Ca 2+apparently rearranges the
./biomed/1471-2105-2-8.txt:1199:          ranges of percent identity. The fraction of alignments
./biomed/1471-2105-3-12.txt:184:            Similarity ranges
./biomed/1471-2105-3-12.txt:189:            user-defined value. Score ranges are related to the
``` 
The first command is running the grep command to find lines with the word "ranges" in .txt files in the biomed directory. The first command prints the file path and the line that contained "ranges," while the command with ```-n``` included the line number before the matching line. (Note that both of these commands were cropped to demonstrate the function and and have more output)  
```
$ grep -n "genetic variation" ./plos/*.txt
./plos/journal.pbio.0020019.txt:8:        amount of genetic variation within the population. This phenotypic constancy led to the
./plos/journal.pbio.0020019.txt:15:        genetic variation without suffering the consequences. If canalization breaks down due to
./plos/journal.pbio.0020019.txt:16:        genetic or environmental circumstances, then the stored genetic variation will be released,
./plos/journal.pbio.0020019.txt:25:        capable of hiding and then releasing genetic variation: (1) individuals heterozygous for
```
In this screenshot ```grep``` searched through the plos directory in order to find "genetic variation." By using ```-n``` the output included the line numbers. (Note the output was cropped)  
```
$ grep -n "valueadded activities" ./government/*/*.txt
./government/Gen_Account_Office/ai00134.txt:43:(3) undertaking other valueadded activities that support strategic
```  
This command searched through text files in the goverment directory in order to find the key phrase "valueadded activities." The output included the line number which is 43. (Note that the (3) coming off after the line number was part of the matching line)  

##  Grep Upper or Lower Case: ```-i```  
When using ```-i``` with grep this will ignore lower vs upper case for the search. This is useful because sometimes the word or phrase you are searching for might be at the beginning of a sentence and could be capitalized.  
```
$ grep "forest service" ./plos/*.txt
./plos/journal.pbio.0020054.txt:        political pressures take over,” Clark says. “That's what a forest service manager's job is,

$ grep -i "forest service" ./plos/*.txt
./plos/journal.pbio.0020054.txt:        political pressures take over,” Clark says. “That's what a forest service manager's job is,
./plos/journal.pbio.0020054.txt:        (USDA) Forest Service policy is much more focused on mechanical means. The argument runs
./plos/journal.pbio.0020054.txt:        characteristics in a given area, says David Peterson of the Forest Service's Pacific
./plos/journal.pbio.0020054.txt:        Forest Service's Fire Sciences Laboratory in Missoula, Montana, researchers have created a
./plos/journal.pbio.0020054.txt:        the regional weather forecasts of so-called mesoscale models. At the Forest Service's Rocky
./plos/journal.pbio.0020054.txt:        Seattle. He's been working for several years with United States Forest Service
```   
The first screenshot is an example of a grep that attempts to find "forest service." The second is the same command but with ```-i``` and yeilds much more results because it just searches for that phrase with disregard to capitalization.  
```
$ grep -i "heart failure" ./biomed/*.txt
./biomed/1468-6708-3-10.txt:        outpatient], heart failure [HF/treated in the hospital or
./biomed/1468-6708-3-10.txt:          Heart Failure Diagnosis
./biomed/1468-6708-3-10.txt:          Heart Failure Diagnostic Criteria
./biomed/1468-6708-3-3.txt:        included stroke, worsening heart failure, need for coronary
# The output was cropped
```    
This example illustrates the different capitalizations that can be found across .txt files. If this command did not include ```-i``` there would be less output values.  
```
$ grep -i "PNEUMONIA" ./biomed/*.txt
./biomed/1468-6708-3-10.txt:          obstructive pulmonary disease (COPD), pneumonia, or other
./biomed/1471-2105-3-37.txt:          Steptococcus pneumonia , 
./biomed/1471-213X-3-3.txt:          Klebsiella pneumoniae [ 45 ] .
./biomed/1471-2148-1-4.txt:          pneumoniae , 
./biomed/1471-2148-1-8.txt:            M. genitalium, M. pneumoniae and
./biomed/1471-2148-1-8.txt:          Chlamydophila pneumoniae (Chlpn),
./biomed/1471-2148-1-8.txt:          Mycoplasma pneumoniae (Mycpn),
./biomed/1471-2148-1-8.txt:            influenzae-P. multocida, C. trachomatis-C. pneumoniae,
./biomed/1471-2148-1-8.txt:            P. horikoshii-P. abyssi, M. genitalium-M. pneumoniae-U.
./biomed/1471-2164-3-33.txt:        Streptococcus pneumoniae , Spy: 
./biomed/1471-2180-1-8.txt:        Pneumocystis carinii causes pneumonia
./biomed/1471-2180-1-8.txt:        P. carinii pneumonia (PcP), and the
```  
In this command I typed the word pneumonia in all caps, however, since I used ```-i``` in the command it still output lines with a matching word. THe output did continue however none included pneumonia in all caps.  

##  Grep Single Word Search: ```-w```  
This command will take a word to search for and only return the matching line if it matches that word and not just contains that word. This is usefull if you are searching for a specific word and not just any word that contains that word. For example, if you are trying to search for apple and do not want it to return something like pineapple then you would use ```-w```.  
```
$ grep -w "pneum" ./biomed/*.txt
# There is no output
```  
As seen in the section above when searching for pneumonia there were a bunch of different lines containing that word in .txt files in the biomed directory. However, if you want to search for a word that is part of pneumonia for example just pneum then by ```-w``` then all the lines of pneumonia will not show up. This is shown in this screenshot.  
```
$ grep -w "apple" ./biomed/*.txt
./biomed/1471-2202-2-5.txt:            computer http://www.apple.com. If the criteria for
./biomed/1471-2458-3-11.txt:        fresh-pressed apple cider [ 28 ] . Other foodborne

$ grep  "apple" ./biomed/*.txt
./biomed/1468-6708-3-10.txt:        questions requiring large sample sizes and to grapple with
./biomed/1471-2105-3-12.txt:            This problem appears to lie in the JAVA applet included
./biomed/1471-2105-3-12.txt:            applet-generated graph may be problematic due to an
./biomed/1471-2105-3-12.txt:            applet incompatibility; capturing the graph as a
./biomed/1471-2202-2-5.txt:            computer http://www.apple.com. If the criteria for
./biomed/1471-2458-3-11.txt:        fresh-pressed apple cider [ 28 ] . Other foodborne
./biomed/1472-6882-1-10.txt:          antibiotics and the ananase enzyme (from the pineapple 
./biomed/gb-2002-3-10-research0053.txt:          in pineapple (~70% to 
./biomed/gb-2002-3-12-research0077.txt:          the JAVA applet WebMol [ 35]. In this setting, the color
./biomed/gb-2003-4-8-r51.txt:            visualized using QuickPDB, a Java applet developed by
```   
This screenshot illustrates the difference between using ```-w``` and not. For the first command when using ```-w``` it only returned lines with apple, while the second command returned lines with words like pineapple as apple is contained in that word.  
```
# This command output has been cropped
$ grep  "earl" ./plos/*.txt
./plos/journal.pbio.0020001.txt:        (SCI). North America and Europe clearly dominate the number of scientific publications
./plos/journal.pbio.0020001.txt:            North America and Europe clearly dominate the number of scientific        
./plos/journal.pbio.0020001.txt:        the top 11–20 (impact factors 3.28–2.47), the Latin American countries contributed nearly
./plos/journal.pbio.0020001.txt:        Nature were nearly identical to those of the top 20 ecological journals.      
./plos/journal.pbio.0020010.txt:        countries would have valued access to JSTOR earlier, but the approach to non-US deals had

$ grep -w "earl" ./plos/*.txt
# There is no output printed
```  
This demonstrates how the word earl is not contained in any of the .txt files in plos but there are many files containing earl.