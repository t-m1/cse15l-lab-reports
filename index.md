# **Lab Report 1**
***
## CD
For all of these cases, the working directory will be /lecture1.

**1) No Arguments**
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
Using cd with no argument takes you back to the starting directory. This output is not an error. 
**2) Path to a directory as an argument**
```
[user@sahara ~/lecture1]$ cd messages/
[user@sahara ~/lecture1/messages]$
```
Using cd with a path to a directory as an argument takes you to that directory. This output is not an error.
**3) Path to a file as an argument**
```
[user@sahara ~/lecture1]$ cd Hello.java 
bash: cd: Hello.java: Not a directory
```
Using cd with a path to a file as an argument that returns an error, which states that Hello.java is not a directory. Since Hello.java is a file, using cd Hello.java won't work.
