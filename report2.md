# **Lab Report 2**

***

## Part 1: ChatServer

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return "Enter a message and user";
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                String[] parameters2 = parameters[1].split("&");
                
                if (parameters2[1].equals("user")){
                    message += String.format("%s: ", parameters[2]);
                }
                if (parameters[0].equals("s")) {
                    message += String.format("%s\n", parameters2[0]);
                    return message;
                }
                
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
![Image](image1.png)
In this first screenshot, `/add-message?s=Hello&user=tmasood` was added to the url. In my code, the `handleRequest` method was called
![Image](image.png)

## Part 2: SSH Key
![Image](private.png)
![Image](public.png)
![Image](nopassword.png)
## Part 3: New Information
Something new that I learned in these labs is that it is possible to run a server using Java. You are also able to modify data on the page by changing the url.
