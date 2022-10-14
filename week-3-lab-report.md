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

We will first run the class SearchEngine to start the server. This is the command we will be using:

```

