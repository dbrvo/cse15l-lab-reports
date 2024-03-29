# Lab Report 2
>Daniel Bravo
>
>CSE 15l

## Part 1
### Code for `ChatServer.java`
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: chat
    String chat = "Chat:\n";
    String line = "";
    String message = "";
    String user = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(chat);
        } else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&");
            String[] messageParameters = parameters[0].split("=");
            if (messageParameters[0].equals("s")) {
                message = messageParameters[1];
                String[] userParameters = parameters[1].split("=");
                if (userParameters[0].equals("user")) {
                    user = userParameters[1];
                    line = user + ": " + message + "\n";
                    chat += line;
                    return String.format("Message: %s \nSent by: %s", message, user);
                }
            } else {
                return "404 Not Found!";
            }
        } else {
            return "404 Not Found!";
        }
        return "404 Not Found!";
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
### Descriptions necessary for each screenshot:
* Which methods in your code are called?
* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

<br />

### Screenshots and Descriptions:
![image](https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/a7812ce9-55d4-47f5-b11f-fd7573e71a8e)
<br />*Figure 1: Web server* `ChatServer` *directly after using* `/add-message?s=Hello&user=jpolitz`
* Prior to running the server, the method `main(String[] args)` of type `void` is called, but once the server is running, and after using `/add-message?s=Hello&user=jpolitz`, the method `handleRequest(URI url)` of type `String` is called.
* For the method `main(String[] args)`, the relevant argument is `args`, and the relevant field of the class `ChatServer` is `port` of type `int` which contains the value of the first value in `args`. For the method `handleRequest(URI url)` the relevant argument is `url` of type `URI`, and the relevant fields of the class `Handler` are `chat`, `line`, `message`, and `user`, which initially equal an empty string `""`.
* Before and after using `/add-message?s=Hello&user=jpolitz`, the values of relevant fields in `ChatServer` do not change because this class only contains the `main` method, which only runs when as the program starts the server. As stated in the previous description, the relevant fields of the class `Handler` have initial values of an empty string `""`, but after using `/add-message?s=Hello&user=jpolitz`, `chat`'s value is itself plus `line`, `line`'s value is `user` plus `": "` plus `message` plus `"\n"`, `message`'s value is `"Hello"`, and `user`'s value is `"jpolitz"`.

<br />
<br />

![image](https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/271405b0-a7a3-434d-a101-3ca0aae18e0f)
<br />*Figure 2: Web server* `ChatServer` *directly after using* `/add-message?s=How are you?&user=dbravo`
* After *Figure 1* and using `/add-message?s=How are you?&user=dbravo`, the method `handleRequest(URI url)` of type `String` is called.
* For the method `handleRequest(URI url)` the relevant argument is `url` of type `URI`, and the relevant fields of the class `Handler` are `chat`, `line`, `message`, and `user`, which initially equal an empty string `""`.
* Before and after using `/add-message?s=How are you?&user=dbravo`, the values of relevant fields in `ChatServer` do not change because this class only contains the `main` method, which only runs when as the program starts the server. As stated in the previous description, the relevant fields of the class `Handler` have initial values of an empty string `""`, but after using `/add-message?s=How are you?&user=dbravo`, `chat`'s value is itself plus `line`, `line`'s value is `user` plus `": "` plus `message` plus `"\n"`, `message`'s value is `"How are you?"`, and `user`'s value is `"dbravo"`.

<br />
<br />

## Part 2
<img width="428" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/c0e393d3-6542-495c-aa4a-a729efd2baef">

The path to the private key for your SSH key for logging into `ieng6` (private key is inside `id_rsa`).

The absolute path should be `/Users/danielbravo/.ssh/id_rsa`

<br />
<br />

<img width="303" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/c1a48028-10f5-4558-828e-942da572b767">

The path to the public key for your SSH key for logging into `ieng6` (public key is inside `authorized_keys`).

The absolute path should be `/home/linux/ieng6/oce/3g/dbravo/.ssh/authorized_keys`

<br />
<br />

<img width="705" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/1367e17a-ebbe-48ee-b22a-55fd13c87e5f">

A terminal interaction where you log into your `ieng6` account *without* being asked for a password.

<br />
<br />

## Part 3
In both labs from weeks 2 and 3 I learned many things I did not know before. For example, for week 2 I had no clue how to run your own web servers from the terminal and a program or how to use the URL to run certain methods in a program. From week 3, I did not know you can use ssh to connect my computer to another. Also, I learned how to make it so I can log in without my password, and I learned a lot more about web servers this week. Most of the things introduced these past few weeks have been completely new, and I have learned many of the basics attaining to these new concepts.
