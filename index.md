# **Lab Report 1**
***
## ```CD```
For all of these cases, the working directory will be /user@sahara/lecture1.

**1) No Arguments**
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
Using `cd` with no argument takes you back to the starting directory, which is also known as the home directory. In this case, the home directory is the user directory user@sahara. This output is not an error.

**2) Path to a directory as an argument**
```
[user@sahara ~/lecture1]$ cd messages/
[user@sahara ~/lecture1/messages]$
```
Using `cd` with a path to a directory as an argument takes you to that directory. This output is not an error.

**3) Path to a file as an argument**
```
[user@sahara ~/lecture1]$ cd Hello.java 
bash: cd: Hello.java: Not a directory
```
Using `cd` with a path to a file as an argument that returns an error, which states that Hello.java is not a directory. Since Hello.java is a file, using `cd Hello.java` won't work.

## ```LS```

**1) No Arguments**

The directory will be /user@sahara/lecture1/messages.

```
[user@sahara ~/lecture1/messages]$ ls
en-us.txt  es-mx.txt  fr.txt  zh-cn.txt
```
Using `ls` with no argument displays the files in the current directory. This output is not an error.

**2) Path to a directory as an argument**

The directory will be /user@sahara/lecture1.

```
[user@sahara ~/lecture1]$ ls messages/
en-us.txt  es-mx.txt  fr.txt  zh-cn.txt
```
Using `ls` with a path to a directory as an argument lists the files that are in the argument directory. In this example, it shows the files in /user@sahara/lecture1/messages because that was the argument. This output is not an error.

**3) Path to a file as an argument**

The directory will be /user@sahara/lecture1.

```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
Using `ls` with a path to a file as an argument just prints the name of the file used as an argument. This is not an error.

## ```CAT```

**1) No Arguments**

The directory will be /user@sahara/lecture1.

```
[user@sahara ~/lecture1]$ cat
Hello World
Hello World
^C
```
Using `cat` with no argument prints whatever was typed in the terminal, and will continue to run until it is terminated, by using ctrl + c. This is not an error because the `cat` command is taking input from the terminal. 

**2) Path to a directory as an argument**

The directory will be /user@sahara/lecture1.

```
[user@sahara ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```
Using `cat` with a path to a directory as an argument prints out an error message stating that ./messages is a directory. `Cat` does not work when using a directory as an argument. 

**3) Path to a file as an argument**

The directory will be /user@sahara/lecture1.

```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
```
Using `cat` with a path to a file as an argument prints out the contents of the file. In this case, it printed out the code that was in the Hello.java file, which is not an error.



