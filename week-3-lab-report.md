# The Simplest Search Engine

## Part 1: The Code

Here is the code needed to create a very basic and simple search engine:

```

class Search implements URLHandler {
    ArrayList<String> stringList = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return stringList.toString();
        }
        else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    stringList.add(parameters[1]);
                    return stringList.toString();
                }
            }
            else if (url.getPath().contains("/search")) {
                ArrayList<String> searchReturn = new ArrayList<>();
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    for (String each: stringList) {
                        if (each.toUpperCase().contains(parameters[1].toUpperCase())) { searchReturn.add(each); }
                    }
                    return searchReturn.toString();
                }
            }
            return "404 Not Found!";
        }
    }
}


class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Search());
    }
}

```

Let's talk about what each piece of code does. We will first create an ArrayList of strings with ``` ArrayList<String> stringList = new ArrayList<>(); ``` . It will be what we return after we carry out our queries. In the ``` handleRequest ``` method, the arguments we take in will be what we type in the URL. 

If the path is empty in the URL, we will return the ArrayList we created, which would include any strings we added into or what we searched for using queries. Now it should be empty because we haven't added any strings into it yet. Here is what it should look like:

![Image](lab2_part1.1.png)

We will first run the class SearchEngine to start the server. Make sure your current directory is wavelet. This is the command we will be using:

```

javac SearchEngine.java 
java SearchEngine 4000
Server Started! Visit http://localhost:4000 to visit.

```
4000 is the port number we will be using. After we run the above commands, you will be given a link. In this case, it is ``` http://localhost:4000 ``` . Type this into your browser. We will be using our search engine there.


## Part 2: Adding

Now, let's try adding stuff into the ArrayList. To add strings into the ArrayList, type in ``` /add?s=<string> ``` after ``` localhost.4000 ``` . This is the part of the code that will run if your path contains ``` /add ``` :

```

if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery.split("=");
                if (parameters[0].equals("s")) {
                    stringList.add(parameters[1]);
                    return stringList.toString();
                }
            }

```

The ``` ? ``` indicates a query and will be recognized by the ``` String[] parameters = url.getQuery().split("="); ``` method, which will then split your input into an array at ``` = ``` . Put anything into ``` <string> ``` . This will be what's added in the ArrayList mentioned earlier. In this case, I typed in ``` /add?s=hi ``` and the result looks like this:

![Image](lab2_part1.2.png)

We can add more to our list:

![Image](lab2_part1.3.png)

## Part 3: Query 

Here's the fun part. Let's run some queries (searches). To do so, type in ``` /search?s=<strings to search> ``` . This is the part of the code that will run when your path contains ``` /search ``` :

```

else if (url.getPath().contains("/search")) {
                ArrayList<String> searchReturn = new ArrayList<>();
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    for (String each: stringList) {
                        if (each.toUpperCase().contains(parameters[1].toUpperCase())) { searchReturn.add(each); }
                    }
                    return searchReturn.toString();
                }
            }

```

It will split what you type in in an array like it did for ``` /run ``` . Then, it will loop through our ArrayList of strings (containing the strings we've added in earlier) and add those containing our queries to a new ArrayList. And this new ArrayList, is what will be returned because it contains what we wanted! Here's an example of me searching for strings containing the letter "i":

![Image](lab2_part1.4.png)

What if we search for something not in the ArrayList? It will reasonably return us an empty ArrayList:

![Image](lab2_part1.5.png)

# Failures and Bugs

## Part 1: ArrayExamples' Bugs

### Failure-inducing Input
There is a problem for our reverseInPlace method here. Here is what a failure-inducing input looks like:

![Image](lab2_part2.1.png)

### Symptoms
We passed in a normal array ``` {1, 4, 6, 2} ``` into the method, expecting it to return ``` {2, 6, 4, 1} ``` . But this is the symptom we got:

![Image](lab2_part2.2.png)

### Bugs
The bug for the reverseInPlace method is that the array itself is changing when we’re trying to access the old values. For example, when we are trying to change the value of the last index to that of the first index, the first index’s value has already been changed to that of the last index, so essentially the last index was not properly grabbing the original value of the first index. Instead, it was just copying its value over to itself, resulting in the improperly reversed array (the symptom).

### Fixes
I created a new array called temp and copied all the elements over to it. Then I assign the values of the end of temp to the front of arr, which reverses arr without changing the original values so they can be copied over successfully, properly returning a reversed ``` arr ``` .

![Image](lab2_part2.3.png)

## Part 2: LinkedList Bug

### Failure-inucing Input
We have a problem for our append method here. This is what a failure-inducing input looks like:

![Image](lab2_part2.4.png)

### Symptoms
The problem occurs when we try to append 4 to the linked list. It gives an out-of-memory error:

![Image](lab2_part2.5.png)

### Bugs
The bug occurs at a while-loop inside the method:

![Image](lab2_part2.6.png)

The while-loop only runs when n.next does not equal to ``` null ``` . The ``` n.next = new Node(value, null) ``` statement is placed inside the while-loop, meaning that n.next will never be null. Hence, it results in an infinite loop, causing the out-of-memory error (the symptom).

### Fixes
To fix it, I put the ``` n.next = new Node(value, null) ``` statement out of the loop, preventing the impossibility of n.next becoming null, eliminating the possibility of an infinite loop. Hence, there will not be an out-of-memory error.

![Image](lab2_part2.7.png)

