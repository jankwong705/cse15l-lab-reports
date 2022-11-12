# Vim Commands

## Part 1: Using VIM to change ``` main ``` method

We are going to use the vim method to change the main method in ``` DocSearchServer.java ``` so instead of restricting ourseleves in searching within the ``` ./technical ``` directory, we can search in whatever path passed in as command-line arguments.

This is the full line of keys we will press. (Only 28!)

```

/port<enter>5ece<right_arrow><right_arrow><backspace><backspace><backspace><backspace>args[1]<esc>:wq 

```

### 1. ``` /port<enter> ``` 
After typing in this command, the cursor will jump to ``` port, ``` which is where we want it to be.
![Image](lab4-part1.1.png)

### 2. ``` 5e ```
The cursor jumps to the directory ``` ./technical ``` which prepares us to delete it efficiently.
![Image](lab4-part2.1.png)

### 3. ``` ce ```
It deletes most of the path except a few characters and enters insert mode for us.
![Image](lab4-part3.1.png)

### 4. ``` <right_arrow><right_arrow> ```
It moves the cursor to an appropriate place where we can conveniently delete the remaining characters.
![Image](lab4-part4.1.png)

### 5. ``` <backspace><backspace><backspace><backspace> ```
It deletes the unwanted leftover characters.
![Image](lab4-part5.1.png)

### 6. ``` args[1] ```
We're changing the code here to " ``` args[1] ``` " !
![Image](lab4-part6.1.png)

### 7. ``` <esc> ```
We're getting out of insert mode here as we have just finished our task.
![Image](lab4-part7.1.png)

### 8. ``` :wq ```
Saving it and exiting vim!
![Image](lab4-part8.1.png)

There we have it! We have successfully made edits using vim within 28 keys!

## Part 2: Seconds Matter

