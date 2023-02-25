# Questionnaire Program
1. ** The first thing you need to do is start the terminal.** Do that by clicking the "hamburger" menu at the top left of the screen, going to the "terminal" section, and clicking "new terminal". Once you open a new one, type `echo hello bash` into the terminal and press enter.
2.  You can run commands in the terminal or put them in a file to be run as a script. You will be making five small programs to learn some scripting. The first one will be a "questionnaire". Use the `touch` command to create `questionnaire.sh` in the `project` folder.
3.  To start, open the file in the main editor by clicking the filename in the left side panel.  

Then, add the text `echo hello questionnaire` at the top of the file. (echo hello questionnaire >> questionnaire.sh)

4.  Your script has one command. Run it with `sh questionnaire.sh` to see what happens. `sh` stands for `shell`.

5.  Using `sh` to run your script uses the `shell` interpreter. Run your script again with `bash questionnaire.sh` to use the `bash` interpreter. `bash` stands for `bourne-again shell`.

6. The output was the same. There are many interpreters which may not give the output you expect. Find out where the `bash` interpreter is located by entering `which bash` in the terminal. (/usr/bin/bash)

7.  That's the absolute path to the `bash` interpreter. You can tell your program to use it by placing a `shebang` at the very top of the file like this: `#!<path_to_interpreter>`. Add a `shebang` at the very top of your file, the one you want looks like this: `#!/bin/bash`.

8.  Now, instead of using `sh` or `bash` to run your script. You can run it by executing the file and it will default to `bash`. Run your script by executing it with `./questionnaire.sh`

9.  You should have got a permission denied message because you don't have permissions to execute the script. List what's in the `project` folder in long list format with `ls -l` to see the file permissions.
```txt
total 8
drwxr-sr-x 3 codeally strove 4096 Oct 28 22:21 learn-bash-scripting-by-building-five-programs
-rw-r--r-- 1 codeally strove   36 Oct 28 22:27 questionnaire.sh
``` 
10. Next to your file is `-rw-r--r--`. All but the first character (`-`) describe permissions different users have with the file. `r` means `read`, `w` means `write`, `x` means `execute`. I don't see an `x` anywhere, so nobody can execute it. Enter `chmod +x questionnaire.sh` in the terminal to give everyone executable permissions.
11. List what's in the folder again with `ls -l` to see the new permissions.
```
drwxr-sr-x 3 codeally strove 4096 Oct 28 22:21 learn-bash-scripting-by-building-five-programs
-rwxr-xr-x 1 codeally strove   36 Oct 28 22:27 questionnaire.sh
```
12.  The `x` was added by each type of user to denote that anyone can execute the file. Run your file again by executing it with `./questionnaire.sh`.
13.  Now it works. In your script, you can add any commands that you would be able to enter in the terminal. Test this by adding the `ls -l` command below your other command.

**How to add?**

Add `ls -l` at the bottom of your `questionnaire.sh` file

14. Run the script by executing it again.
```sh
hello questionnaire
total 8
drwxr-sr-x 3 codeally strove 4096 Oct 28 22:21 learn-bash-scripting-by-building-five-programs
-rwxr-xr-x 1 codeally strove   42 Oct 28 22:29 questionnaire.sh
```
15. Your script printed the result of the two commands as if you entered them in the terminal. Delete everything but the `shebang` from your file so you can start making the questionnaire.
16. Bash has variables, functions, and other things you might be familiar with. You can create a variable with `VARIABLE_NAME=VALUE`. There cannot be any spaces around the equal (`=`) sign. If a variable has any spaces in it, place double quotes around it. Create a variable named `QUESTION1` and set it's value to `"What's your name?"`.

**How to add?**

Add `QUESTION1="What's your name?"` at the bottom of your `questionnaire.sh` file

17. To use a variable, place `$` in front of it like this: `$VARIABLE_NAME`. Shell scripts run from top to bottom, so you can only use variable below where it's created. Use `echo` to print your variable.

**How to add?**

Add `echo $QUESTION1` at the bottom of your `questionnaire.sh` file

18. Run the file like you did before to see if it worked. You can see question What's your name?
19. The question was printed. Next, you want to be able to accept input from a user. You can do that with `read` like this: `read VARIABLE_NAME`. This will get user input and store it into a new variable. After you print the question, use `read` to get input and store it in a variable named `NAME`.

**How to add?**

Add `read NAME` at the bottom of your `questionnaire.sh` file

20.  At the bottom of your script, use `echo` to print `Hello <name>.` to the terminal.
```sh
#!/bin/bash

  

QUESTION1="What's your name?"

  

echo  $QUESTION1

read NAME

  

echo Hello $NAME.
```
21. Run the file again. Type your name and press enter after it asks for it.
````txt
What's your name?
Quang Anh
Hello Quang Anh.
````
22. Right below your first variable, create another one named `QUESTION2`. Set the value to, `Where are you from?`. Make sure to put it in double quotes.
23. After your `read` command, use your new variable to print the next question.
24. Below where the second question is printed, use `read` to get input from the user into a variable named `LOCATION`.

**How to add?**

Add `read LOCATION` to your script below `echo $QUESTION2`

25. Change the existing response to `Hello <name> from <location>.`

**How to add?**

The suggested command should look like: `echo Hello $NAME from $LOCATION.`

26. Run the script and enter values when it is waiting for input.
```txt
What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
```
27. It's looking good. I want a title to appear when the program first starts. Use `echo` to print `~~ Questionnaire ~~` before anything else is printed.

**How to add?**

Add `echo ~~ Questionnaire ~~` below your `shebang`

28. Run the script and enter values until it is done again so you can see what the title looks like.
```txt
What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
~~ Questionnaire ~~
```
29. It would be nice if there was some empty lines around the title. You've probably used the `--help` flag before, see if you can use it with `echo` to try and find a way to add empty lines.
30. That didn't work as I hoped. Another way to find information about a command is with `man`. It stands for `manual` and you can use it like this: `man <command>`. See if there's a manual for `echo`.
31. At the top of the menu, the `-e` option looks promising. And the `\n` below it says `new line`. You should take a look at those. In your script, change the title to `echo -e \n~~ Questionnaire ~~\n` to see if that prints the empty lines.

Change the suggested line to `echo -e \n~~ Questionnaire ~~\n`

32. Run it to see if it worked. You can press `ctrl+c` to close the program after it starts if you don't want to enter values.
```txt
What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
n~~ Questionnaire ~~n
```
33. It didn't print the empty lines. `echo` will only print empty lines if the value is enclosed in quotes. Place double quotes around the title that gets printed to see if it works.

Change the suggested line to `echo -e "\n~~ Questionnaire ~~\n"`
```sh
#!/bin/bash
echo -e "\n~~ Questionnaire ~~\n"
QUESTION1="What's your name?"
echo  $QUESTION1
read NAME
echo Hello $NAME.
QUESTION2="Where are you from?"
echo  $QUESTION2
read LOCATION
echo Hello $NAME from $LOCATION.
```
34. Run your script again to see if that fixed it.
```txt
~~ Questionnaire ~~

What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
```
35. Now it's working 😄 Create a `QUESTION3` variable next to the other two, set it's value to `"What's your favorite coding website?"`
36. Use `echo` to print the third question after you `read` the `LOCATION`.
37. After the question you just printed, add code to read input into a variable named `WEBSITE`.

**How to add?**

Add `read WEBSITE` below the `echo $QUESTION3`

38. Change the `echo` command of the response to print this sentence instead: `Hello <name> from <location>. I learned that your favorite coding website is <website>!`

The command should look like this: `echo Hello $NAME from $LOCATION. I learned that your favorite coding website is $WEBSITE!`

39. Run the script and enter values when the program is waiting. Let's see the final output.
```txt
~~ Questionnaire ~~

What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
What's your favorite coding website?
freecodecamp.org
Hello Quang Anh from Vietnam. I learned that your favorite coding website is freecodecamp.org!
```
40. One last thing. Change that final response to print an empty line at the beginning of the sentence.

**How to add?**

- Use  `echo`  with the  `-e`  flag and a new line (`\n`) character like you did for the title
- Don't forget to put the response in double quotes so it prints the empty line
- Here's an example:  `echo -e "\n<message>"`
- Only add a new line at the beginning of the response, not the end
- The final command should look like this:  `echo "\nHello $NAME from $LOCATION. I learned that your favorite coding website is $WEBSITE!"`

```sh
echo -e "\nHello $NAME from $LOCATION. I learned that your favorite coding website is $WEBSITE!"
```
41. Run it one last time and enter values when it asks to see if you like how it looks. 
```sh
~~ Questionnaire ~~

What's your name?
Quang Anh
Hello Quang Anh.
Where are you from?
Vietnam
Hello Quang Anh from Vietnam.
What's your favorite coding website?
freecodecamp.org

Hello Quang Anh from Vietnam. I learned that your favorite coding website is freecodecamp.org!
```
# Program that counts down to zero from a given argument
42. It looks good. I think you are done with that script for now. The next program will be countdown timer. Use the `touch` command to create a new file named `countdown.sh` in your `project` folder.
43. Give your file executable permissions so you can run it like the other one. It's the `chmod` command with the `+x` flag.
44. You want to use the `bash` interpreter again. Add a `shebang` at the top of your new file to denote that.
45. Comments in `bash` look like this: `# <comment>`. Add a comment below the `shebang` that says `Program that counts down to zero from a given argument` so people know what it does. Note that the `shebang` is a special case and is not treated like a comment.
46. Programs can take arguments. You can access them a few different ways with `$`. Add `echo $*` in your script to print all arguments passed to it.
47. Execute your script with `./countdown.sh`.
48. Nothing was printed. Run your script again, but this time add three arguments to the command; `arg1`, `arg2`, and `arg3`. Place them after the command with a space before each one.

**How to print?***

Type `./countdown.sh arg1 arg2 arg3` in the terminal and press enter

49. `$*` printed all the arguments passed to your script. To access any one of them, use `$<number>`. `arg2` could have been accessed with `$2`. Change your script to `echo` the first argument instead of all the arguments.

**How to change code?**

- Try running your script with an argument to make sure it’s giving the expected output
- Use  `echo $1`  to print the second argument
- Change  `echo $*`  to  `echo $1`  in your  `countdown.sh`  file

50. Run your file with `./countdown.sh arg1 arg2 arg3` again.
51. Now it just prints the first argument. Your program will accept an argument to count down from. You will test it with an `if` statement to make sure it's a positive integer. I wonder what that syntax would look like. Type `help` in the terminal to see if you can find anything.
52. This is a list of built-in commands. You should look over it, some of them may look familiar. I see `echo` in there. Another one is `if`. See if you can find out more about it by checking its `man` page. (there is no manual entry for if)
53. I guess there isn't a `man` page for it. At the top of the `help` screen, I noticed you can use `help <command>` to find out more. Yet another way to find out about a command 😥 See if you can find out more about `if` with that method.
```txt
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.
    
    The `if COMMANDS' list is executed.  If its exit status is zero, then the
    `then COMMANDS' list is executed.  Otherwise, each `elif COMMANDS' list is
    executed in turn, and if its exit status is zero, the corresponding
    `then COMMANDS' list is executed and the if command completes.  Otherwise,
    the `else COMMANDS' list is executed, if present.  The exit status of the
    entire construct is the exit status of the last command executed, or zero
    if no condition tested true.
    
    Exit Status:
    Returns the status of the last command executed.
```
54.   
The syntax is at the top, not all of it is required. Here's another example:
```sh
if [[ CONDITION ]]
then
  STATEMENTS
fi
```
Remove the  `echo $1`  in your script and add an  `if`  condition that checks  `if [[ $1 == arg1 ]]`. In its  `then`  area, use  `echo`  to print  `true`  to the screen. There must be spaces on the inside of the brackets (`[[ ... ]]`) and around the operator (`==`).

**How to remove?**

- Make sure to remove the  `echo $1`
- Add the following to your  `countdown.sh`  file:
```sh
if [[ $1 == arg1 ]]
then
  echo true
fi
```
55. Notice that the end of the syntax is `fi` (`if` backwards). It should print `true` if you pass `arg1` to your script now. Run the script with `arg1` as the only argument.

**How to run?**

Type `./countdown.sh arg1` in the terminal and press enter. It is true

56. The `if` condition worked, it printed `true`. Run it again with anything except `arg1` as the first argument.
57. Nothing was printed. One of the optional parts of  `if`  was an  `else`  area. You can use it like this:

```sh
if [[ CONDITION ]]
then
  STATEMENTS
else
  STATEMENTS
fi

```

Add an  `else`  to your existing  `if`  condition. Use  `echo`  to print  `false`  if the condition fails.

Your  `if`  should look like this:
```sh
if [[ $1 == arg1 ]]
then
  echo true
else
  echo false
fi
```
58. Run the script again and use anything except `arg1` as the only argument. It print to false
59. Now it printed `false`. Your program is expecting an integer to count down from as its argument. You can compare integers inside the brackets (`[[ ... ]]`) of your `if` with `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-le` (less than or equal), `-gt` (greater than), `-ge` (greater than or equal). Change your `if` condition to check if your first argument is less than `5`.

**How to change?**
- Make sure there's spaces inside the brackets (`[[ ... ]]`) and around the operator (`-lt`)
- Your  `if`  condition should look like this:  `[[ $1 -lt 5 ]]`
- The whole  `if`  should look like this:
```sh
if [[ $1 -lt 5 ]]
then
  echo true
else
  echo false
fi
```
60. Run the script again and use `4` as a first argument to make sure it's working. (it print to true)
61. It printed `true` since your argument was less than `5`. Run it again with `5` as the argument. (it prints to false)
62. As expected, that printed `false`. Take a look at that `help` menu again. I want to see if we can find out more about how these expressions work.
63. Near the top left, it says `[[ expression ]]`. Those look like the double brackets you are using. See if you can get more info about that with the `help` command like you did with `help if`.
64. Near the top left, it says `[[ expression ]]`. Those look like the double brackets you are using. See if you can get more info about that with the `help` command like you did with `help if`.

**How print help?**
- Here's an example:  `help <command>`
- Type  `help [[ expression ]]`  or  `help [[`  in the terminal and press enter
```txt
[[ ... ]]: [[ expression ]]
    Execute conditional command.
    
    Returns a status of 0 or 1 depending on the evaluation of the conditional
    expression EXPRESSION.  Expressions are composed of the same primaries used
    by the `test' builtin, and may be combined using the following operators:
    
      ( EXPRESSION )    Returns the value of EXPRESSION
      ! EXPRESSION              True if EXPRESSION is false; else false
      EXPR1 && EXPR2    True if both EXPR1 and EXPR2 are true; else false
      EXPR1 || EXPR2    True if either EXPR1 or EXPR2 is true; else false
    
    When the `==' and `!=' operators are used, the string to the right of
    the operator is used as a pattern and pattern matching is performed.
    When the `=~' operator is used, the string to the right of the operator
    is matched as a regular expression.
    
    The && and || operators do not evaluate EXPR2 if EXPR1 is sufficient to
    determine the expression's value.
    
    Exit Status:
    0 or 1 depending on value of EXPRESSION.
```
65. It might not be a bad idea to read that. Looks like you can use some, probably familiar, things like `!`, `&&`, and `||` to compare multiple expressions. There's also `==` and `!=` operators for an individual expression. It says something about the `test` built-in command. See if you can bring up the `help` menu for that.

**How to help?**

- View the  `help`  menu of the suggested command like you did for the  `help if`
- Here's an example:  `help <command>`
- Type  `help test`  in the terminal and press enter

```txt
test: test [expr]
    Evaluate conditional expression.
    
    Exits with a status of 0 (true) or 1 (false) depending on
    the evaluation of EXPR.  Expressions may be unary or binary.  Unary
    expressions are often used to examine the status of a file.  There
    are string operators and numeric comparison operators as well.
    
    The behavior of test depends on the number of arguments.  Read the
    bash manual page for the complete specification.
    
    File operators:
    
      -a FILE        True if file exists.
      -b FILE        True if file is block special.
      -c FILE        True if file is character special.
      -d FILE        True if file is a directory.
      -e FILE        True if file exists.
      -f FILE        True if file exists and is a regular file.
      -g FILE        True if file is set-group-id.
      -h FILE        True if file is a symbolic link.
      -L FILE        True if file is a symbolic link.
      -k FILE        True if file has its `sticky' bit set.
      -p FILE        True if file is a named pipe.
      -r FILE        True if file is readable by you.
      -s FILE        True if file exists and is not empty.
      -S FILE        True if file is a socket.
      -t FD          True if FD is opened on a terminal.
      -u FILE        True if the file is set-user-id.
      -w FILE        True if the file is writable by you.
      -x FILE        True if the file is executable by you.
      -O FILE        True if the file is effectively owned by you.
      -G FILE        True if the file is effectively owned by your group.
      -N FILE        True if the file has been modified since it was last read.
    
      FILE1 -nt FILE2  True if file1 is newer than file2 (according to
                       modification date).
    
      FILE1 -ot FILE2  True if file1 is older than file2.
    
      FILE1 -ef FILE2  True if file1 is a hard link to file2.
    
    All file operators except -h and -L are acting on the target of a symbolic
    link, not on the symlink itself, if FILE is a symbolic link.
    
    String operators:
    
      -z STRING      True if string is empty.
    
      -n STRING
         STRING      True if string is not empty.
    
      STRING1 = STRING2
                     True if the strings are equal.
      STRING1 != STRING2
                     True if the strings are not equal.
      STRING1 < STRING2
                     True if STRING1 sorts before STRING2 lexicographically.
      STRING1 > STRING2
                     True if STRING1 sorts after STRING2 lexicographically.
    
    Other operators:
    
      -o OPTION      True if the shell option OPTION is enabled.
      -v VAR         True if the shell variable VAR is set.
      -R VAR         True if the shell variable VAR is set and is a name
                     reference.
      ! EXPR         True if expr is false.
      EXPR1 -a EXPR2 True if both expr1 AND expr2 are true.
      EXPR1 -o EXPR2 True if either expr1 OR expr2 is true.
    
      arg1 OP arg2   Arithmetic tests.  OP is one of -eq, -ne,
                     -lt, -le, -gt, or -ge.
    
    Arithmetic binary operators return true if ARG1 is equal, not-equal,
    less-than, less-than-or-equal, greater-than, or greater-than-or-equal
    than ARG2.
    
    See the bash manual page bash(1) for the handling of parameters (i.e.
    missing parameters).
    
    Exit Status:
    Returns success if EXPR evaluates to true; fails if EXPR evaluates to
    false or an invalid argument is given.
```
66. That's what I was looking for. At the top are some file operators. There's some string and other operators as well. You should take a look at them. Near the bottom, are the arithmetic operators you used with your `if` condition. Change the condition in your script to check if the first argument is less than or equal to `5`.

The `if` condition should look like this: `[[ $1 -le 5 ]]`

67. Run the script and use `5` as a first argument again. (it prints to true)
68. Now it prints `true`. Remember I said any command can run in the terminal or a script. Try running an expression right in the terminal by entering `[[ 4 -le 5 ]]` in it.
69. Nothing happened? Each command has an exit status that can be accessed with `$?`. View the exit status of the **last command** with `echo $?`.

**How to view**

Type `echo $?` in the terminal and press enter (print to 0).

70. The exit status of `0` means it was true, `4` is indeed less or equal to `5`. Try it again with `[[ 4 -ge 5 ]]`.
71. Use `echo $?` to view the exit status of the command you just entered. (It print to 1).
72. It printed `1` this time for false. You can separate commands on a single line with `;`. Enter your last two commands on one line like this: `[[ 4 -ge 5 ]]; echo $?`. It will run the expression, then print the exit status of it since it was the last command. (it is 1).
73. It's still false. Using the same syntax of `[[ ... ]]; echo$?`, check if `10` is not equal to `5` and print the exit status of the expression on one line.

**How to print?**

- Check the  `help test`  menu to find the  `not equal`  operator
- It's the  `-ne`  operator
- You previously used  `[[ 4 -ge 5 ]]; echo $?`
- Make sure there's spaces inside the brackets and around the operator
- Type  `[[ 10 -ne 5 ]]; echo $?`  in the terminal and press enter. It print to 0.

74. You can think of an exit status of `0` as true. But it means that the command had zero errors. All commands have an exit status. Using the same syntax, enter `bad_command;` and check its exit status on a single line.

**How to print?**

Type `bad_command; echo $?` in the terminal and press enter

Output:
```txt
bash: bad_command: command not found
127
```
75. `command not found`, with an exit status of `127`. Anything but `0` means there was an error with the command. `bad_command` didn't exist. Try it again with `ls`. It print list file and return 0.
```txt
countdown.sh  learn-bash-scripting-by-building-five-programs  questionnaire.sh
0
```
76. The command executed as expected and there were zero errors. So it gave you an exit status of `0`. Try it again with `ls -y`. It was error and return 2.
```txt
ls: invalid option -- 'y'
Try 'ls --help' for more information.
2
```
77. The `-y` flag doesn't work with `ls` so it gave you an exit status other than `0`, meaning that the command was unsuccessful. View the `help` menu of the `test` command again, I want to see what else is in that list.
78. You tried a few of the arithmetic operators, those work for integers. Try one of the file operators. The first one on the list checks if a file exists. Type `[[ -a countdown.sh ]]; echo $?` in the terminal to see if your file exists. It return to 0.
79. The file must exist. It's checking the folder the command is entered from. Try it again with `bad_file.txt`. It return to 1.

**How to check?**

Type `[[ -a bad_file.txt ]]; echo $?` in the terminal and press enter

80. `bad_file.txt` doesn't exist. I think you're getting the hang of this. Using the same syntax, check if you have permissions to execute your `countdown.sh` file. You may want to look at that menu again.

**How to return?**

Type `[[ -x countdown.sh ]]; echo $?` in the terminal and press enter. It return to 0.

81. You played around with a number of the expressions. View the `help [[ expression ]]` menu again that you looked at before to see a few more options. You can view the menu with just `help [[`.
82. As I mentioned before, you can test multiple expressions with `&&` and `||`. Enter `[[ -x countdown.sh && 5 -le 4 ]]; echo $?` in the terminal to test the file is executable by you **and** five is less than or equal to four. It return to 1.
83. Both conditions weren't true, so the exit status was `1` for `false`. Try testing the same two conditions with the `or` operator.

**How to return?**

Modify this `[[ -x countdown.sh && 5 -le 4 ]]; echo $?` with the suggestion and enter it in the terminal. It return to 0.

84. One of the conditions was true so it printed `0`. I think that's enough of a detour. Back in your script, change the `if` condition to check if the first argument is **greater than zero** so you can be sure it's something you can count down from. (countdown.sh file)

**How to change code?**

The `if` condition should look like this: `[[ $1 -gt 0 ]]`

85. The condition you added checks if a positive integer was passed as an argument to the script and executes the `then` area. Change the existing `echo` command to print `Include a positive integer as the first argument.` if a positive integer is not used.

The whole `if` condition should look like this:
```sh
if [[ $1 -gt 0 ]]
then
  echo true
else
  echo Include a positive integer as the first argument.
fi
```
86. Run your script and use `1` as a first argument to make sure the condition is working.

Type `./countdown.sh 1` in the terminal and press enter. It return true.

87. Run it again and use anything but a positive integer as the only argument.

Type `./countdown.sh 0` in the terminal and press enter. It return "Include a positive integer as the first argument."

88. Looks like your `if` condition is working. Next, you want to loop over the argument and count down to zero from it. Check the `help` menu to see if there's any commands for this.
89. There's two  `for`  loops in there, you want the second one. Here's an example:
```sh
for (( i = 10; i > 0; i-- ))
do
  echo $i
done
```
The above creates a variable (`i = 10`), then prints it, subtracts one, and repeats until  `i`  is not greater than  `0`. So it prints  `10`  through  `1`. In the  `then`  area of your condition, replace the  `echo`  with a  `for`  loop that prints from the argument (`$1`) to  `1`.

**How to solve?**

- Set the variable to the value of your argument (`$1`) initially
- Use the same syntax as the example except change the  `10`  to  `$1`
- Don't include any extra commands in the  `then`  area
- Your  `then`  area should look like this:
```sh
for (( i = $1; i > 0; i-- ))
do
  echo $i
done
```
- The whole  `if`  condition should look like this:
```sh
if [[ $1 -gt 0 ]]
then
  for (( i = $1; i > 0; i-- ))
  do
    echo $i
  done
else
  echo Include a positive integer as the first argument.
fi
```
90. Run your script and use `10` as the first argument.  It return "Include a positive integer as the first argument."
91. It works 😄 But I want it to pause for one second between each number. Check the `help` menu again to see if there's any commands that might help.
92. I'm not seeing the command I was hoping to. These are the built-in commands, where are the rest? Type `ls /` to look around.
```txt
bin   dev  home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  etc  lib   lib64  media   opt  root  sbin  sys  usr
```
93. The `/` listed what's in the root of the file system. I see a `bin` folder, `bin` stands for `binary`. View what's in it with `ls /bin`.\
94. These are some non built-in commands. There's quite a few that should look familiar. One is `bash`, that's the one you used for the `shebang` in your scripts. I see one called `sleep`. View the manual of it.
95. At the top, it says you can pause execution for a number of seconds. Try it out by entering `sleep 3` in the terminal.
96. That should work. In your `for` loop, use `sleep` to make the script pause for `1` second after each number is printed.
```sh
if [[ $1 -gt 0 ]]
then
  for (( i = $1; i > 0; i-- ))
  do
    echo $i
    sleep 1
  done
else
  echo Include a positive integer as the first argument.
fi
```
97. Run your script and use `3` as the first argument. It return countdown from 3 to 1
98. Awesome. Except it should print `0` instead of stopping at `1`. Change the condition in your for loop so that it checks for `i >= 0`.
99. Run your script with `3` as the argument again. It return countdown from 3 to 0.
100. Excellent. I want it to display a title like the other script. Make it so that it prints `~~ Countdown Timer ~~` before anything else. Include a new line before and after it like you did for the other title. 

```sh
echo -e "\n~~ Countdown Timer ~~\n"
```
101. Run your script and use `1` as the first argument again to see the title.
```txt
~~ Countdown Timer ~~

1
0
```
102. This is fun. You can create a multiline comment like this:
```sh
: '
  comment here
  more comment here
'
```
Comment out your  `for`  loop with a multiline comment. I want to try and do this with a  `while`  loop.

**How to comment multi-line?**

- Comment out the  `for`  loop in your  `countdown.sh`  file with a multiline comment
- Make sure there's a space between the  `:`  and  `'`
- Your  `for`  loop should look like this:
```sh
: '
for (( i = $1; i >= 0; i-- ))
do
  echo $i
  sleep 1
done
'
```
103. View the `help` menu for the `while` command to see if you can find anything.
```txt
while: while COMMANDS; do COMMANDS; done
    Execute commands as long as a test succeeds.
    
    Expand and execute COMMANDS as long as the final command in the
    `while' COMMANDS has an exit status of zero.
    
    Exit Status:
    Returns the status of the last command executed.
```
104. It shows the syntax. First, below your comment, create a variable named `I` that is set to the value of your first argument. It will start there, then on each iteration of the `while` loop you can subtract `1` from it until it reaches `0`.

**How to add?**

- Add  `I=$1`  in the  `then`  area of your  `if`  statements below the multi-line comment
- The  `then`  area should look like this:
```sh
: '
for (( i = $1; i >= 0; i-- ))
do
  echo $i
  sleep 1
done
'
I=$1
```
105. The menu showed that you can make a  `while`  loop like this:
```sh
while [[ CONDITION ]]
do
  STATEMENTS
done
```
Add a  `while`  loop below the  `I`  variable you made. The condition should be  `$I -ge 0`  and you should  `echo`  the  `I`  variable in the  `do`  statements.

**How to add while loop?**

Your  `while`  loop should look like this:
```sh
while [[ $I -ge 0 ]]
do
  echo $I
done
```
Here full source code:
```sh
echo -e "\n~~ Countdown Timer ~~\n"

if [[ $1 -gt 0 ]]
then
  : '
  for (( i = $1; i >= 0; i-- ))
  do
    echo $i
    sleep 1
  done
  '
  I=$1
  while [[ $I -ge 0 ]]
  do
    echo $I
  done
else
  echo Include a positive integer as the first argument.
fi
```
105. `I` never changes here, so you would have an infinite loop. You can subtract one from `I` with double parenthesis (`((...))`) and the `--` operator. In your while loop, add `(( I-- ))` after you `echo $I` to subtract one from `I` on each pass.

Your  `while`  loop should look like this:
```sh
while [[ $I -ge 0 ]]
do
  echo $I
  (( I-- ))
done
```
106. The last thing to do is to add the `sleep` again. In your `while` loop, add the code to make it `sleep` for `1` second. Add the code after the `(( I-- ))`.

Your  `while`  loop should look like this:
```sh
while [[ $I -ge 0 ]]
do
  echo $I
  (( I-- ))
  sleep 1
done
```
Here full source code:
```sh
#!/bin/bash

# Program that counts down to zero from a given argument

echo -e "\n~~ Countdown Timer ~~\n"

if [[ $1 -gt 0 ]]
then
  : '
  for (( i = $1; i >= 0; i-- ))
  do
    echo $i
    sleep 1
  done
  '
  I=$1
  while [[ $I -ge 0 ]]
  do
    echo $I
    (( I-- ))
    sleep 1
  done
else
  echo Include a positive integer as the first argument.
fi
```
# Bingo Number Generator Program
107. Run the script and use 5 as the first argument.
108. I think the countdown timer is finished. Feel free to try it with some other arguments. The next one is a bingo number generator. Use `touch` to create `bingo.sh` in the same folder as the others.
109. Give your file executable permissions like you did for the other two.
```txt
chmod +x bingo.sh
```
110.  Add a `shebang` at the top of your new script. It should use `bash` again like other two.
111. Add a comment below the `shebang` that says, `Bingo Number Generator`.
112. Before I forget, use a single `echo` command to print a title for this program. It should say `~~ Bingo Number Generator ~~` with an empty line before and after it.
113. In your script, create a `NUMBER` variable that equals `5`.

Add `NUMBER=5` to the bottom of your `bingo.sh` file

114. Below your new variable, use `echo` to print it to the screen.

Add `echo $NUMBER` at the bottom of your `bingo.sh` file

115. Run the script by executing it. (It print to 5)
116. The numbers in bingo go up to 75, each number has a letter from the word `bingo` associated with it. You will need to randomly generate a number between 1 and 75. Bash may have something that can help you here. A shell comes with environment variables. View them by entering `printenv` in the terminal.
117. These are all environment variables, they are predefined and loaded with each shell. Most of them aren’t very relevant, but it’s nice to know they’re there. One of them is `LANG`. Use `echo` to print it in the terminal.

Type `echo $LANG` in the terminal and press enter (it print en_US.UTF-8).

118. View all variables in the shell with `declare -p`. `-p` stands for `print`
119. This list includes all the environment variables, and any others that may have been created in the current shell. There's one named `RANDOM`. Use `echo` to print it in the terminal.

Type `echo $RANDOM` in the terminal and press enter. It print 17338.

120. Back in your script, use the `RANDOM` variable to set `NUMBER` to a random number instead of `5`.

**How to change?**

Change `NUMBER=5` to `NUMBER=$RANDOM`

121. Run the script a few times in a row to make sure it's working. It print randomly number.
122. The `RANDOM` variable will generate a random number between 0 and 32767. You can use the `modulus` operator to make it in the range you want. In your script, change the `NUMBER` variable to `$RANDOM%75`.
123. Run the script again.
124. Bash sees everything as a string so it just printed the `%75` part literally. In the terminal, create an `I` variable equal to `0` (zero), so you can play with it and figure out how to do some calculations.
125. In the terminal, use `echo` to print your new variable. It return to 0
126. I noticed that you used double parenthesis in the `while` loop of your countdown timer to subtract one from `I`. Type `(( I++ ))` in the terminal to see if anything happens.
127. There was no output. Use `echo` to print `I` in the terminal again. It return to 1
128. The double parenthesis performed the calculation, changing the value of `I` from `0` to `1`. Enter `help let` in the terminal to see the operators you can use with the double parenthesis.
129. You used several of these now, including in the `for` loop from the countdown timer. Enter `(( I += 10 ))` in the terminal to increment `I` by `10`. Note that you don't need to prepend variables with `$` inside these parenthesis.
130. Use `echo` to print your `I` variable again. It return to 11.
131. It should have printed `11` for the value of `I`. Using the double parenthesis like you have been is good for changing variable values or making comparisons. It makes the calculation in place and provides no output. If you want to make a calculation and do something with the result, add a `$` in front like this: `$(( ... ))`. Type `$(( I + 4 ))` in the terminal to see what happens.
132. It should have printed `11` for the value of `I`. Using the double parenthesis like you have been is good for changing variable values or making comparisons. It makes the calculation in place and provides no output. If you want to make a calculation and do something with the result, add a `$` in front like this: `$(( ... ))`. Type `$(( I + 4 ))` in the terminal to see what happens.

It was error (bash: 15: command not found)

133. It should say, `bash: 15: command not found`. It replaced the command with the result of the calculation. Effectively, trying to run `15` as a command. Enter the same command, but put `echo` in front of it. The command was `$(( I + 4 ))`. It returns to 15.
134. Again, it replaced the calculation with the result. So it was basically the same as if you entered `echo 15`. Use `echo` to print `I` to the screen again. It return to 11.
135. It should still have printed `11` for `I`. See the hints if it didn't. These double parenthesis with a `$` are how you can assign a variable to some calculation. In the terminal, create a `J` variable, and use the `$(( ... ))` syntax to set its value to `I - 6`.

**How to type?**

Type `J=$(( I - 6 ))` in the terminal and press enter

136. Use `echo` to print `J`. It return to 5.
137. `J` should equal `5`. For some more practice, use `echo` to print the value `J * 5 + 25`.

**How to type?**

Type `echo $(( J * 5 + 25 ))` in the terminal and press enter. It return to 50.

138. It should have printed `50`. Print `J` with `echo` again. It print to 5.
139. So, as a reminder, `(( ... ))` will perform a calculation or operation and output nothing. `$(( ... ))` will replace the calculation with the result of it. You made a few variables in this shell, view them with `declare -p`.
140. `declare` can be used to create variables, but you are just going to use it to view them for now. If you scroll up a little, you should find your `I` and `J` variables in there. View `J` with `declare -p J`. It print `declare -- J="5"`
141. I saw `RANDOM` in that list, too. View it with `declare -p <variable>` like you did for `J`.

**How to print?**

Type `declare -p RANDOM` in the terminal and press enter. It print randomly (declare -i RANDOM="10265")

142. Okay, I think I finally know how to get the random number for the Bingo Number Generator. Use `echo` and `RANDOM % 75` to print a random number in the terminal.

**How to print?**

Type `echo $(( RANDOM % 75 ))` in the terminal and press enter. It print to randomly number.

143. One tiny problem, that calculation will give a number between 0 and 74. Enter the same command in the terminal, but add `1` to the calculation to get a random number between 1 and 75.

Type `echo $(( RANDOM % 75 + 1 ))` in the terminal and press enter

144. Back in your `bingo.sh` script, change the `NUMBER` variable so that it starts as a random number between 1 and 75 using the syntax you have been practicing.

It should look like this: `NUMBER=$(( RANDOM % 75 + 1 ))`

145. Run your script a few times in a row to make sure it's working. It worked!
146. Next, create a `TEXT` variable and set the value to `"The next number is, "`. When the script is finished, the output will be something like `The next number is B:15`.
147. Next, create a `TEXT` variable and set the value to `"The next number is, "`. When the script is finished, the output will be something like `The next number is B:15`.
148. The letter that goes with the random number depends on what the number is. If it's 15 or less, it will be a `B`. I saw some comparisons in the `help let` menu, take a look at it again.
149. You used the double square brackets with your `if` statement in the last program, but you can use the double parenthesis with these operators as well. In your script, create an `if` statement that uses double parenthesis for the condition. Check if the number variable is less than or equal to 15. If it is, use your two variables to print `The next number is, B:<number>`.

**How to check?**

- Make sure you only have two  `echo`  statements in your script, the title being one of them
- Here's an example of how your  `if`  statement should look:
```sh
if (( CONDITION ))
then
  STATEMENTS
fi
```
- The condition you want is  `(( NUMBER <= 15 ))`
- In the statements area, use  `echo`  and your two variables to print  `The next number is, B:<number>`
- The statements area should look like this:  `echo $TEXT B:$NUMBER`
- The whole  `if`  statement should look like this:
```sh
if (( NUMBER <= 15 ))
then
  echo $TEXT B:$NUMBER
fi
```
150. `if`  statements can have an "else if" area like this:
```sh
if (( CONDITION ))
then
  STATEMENTS
elif [[ CONDITION ]]
then
  STATEMENTS
fi
```
Using the double square brackets this time, add an  `elif`  condition that checks if the number variable is less than or equal to  `30`. If it is, use your two variables again to print  `The next number is, I:<number>`

**How to change code?**

- View the  `help test`  menu to see the operators you can use with the double square brackets
- The condition you want is  `[[ $NUMBER -le 30 ]]`. Don't forget the  `$`
- In the statements area, use  `echo`  and your two variables to print  `The next number is, I:<number>`
- The statements area should look like this:  `echo $TEXT I:$NUMBER`
- The  `elif`  area should look like this:
```sh
elif [[ $NUMBER -le 30 ]]
then
  echo $TEXT I:$NUMBER
fi
```
151. You can add as many `elif` sections to an `if` statement as you want. Add another `elif`, below the last, one that uses the double parenthesis to check if the number variable is less than 46. If it is, use your two variables to print `The next number is, N:<number>`

**How to change code?**

- View the  `help let`  menu to see the operators you can use with the double parenthesis
- The operator you want it  `<`
- You can add another  `elif`  like this:
```sh
if CONDITION
then
  STATEMENTS
elif CONDITION
then
  STATEMENTS
elif CONDITION
then
  STATEMENTS
fi
```
- The condition you want is  `(( NUMBER < 46 ))`
- In the statements area, use  `echo`  and your two variables to print  `The next number is, N:<number>`
- The statements area should look like this:  `echo $TEXT N:$NUMBER`
- This  `elif`  area should look like this:
```sh
elif (( NUMBER < 46 ))
then
  echo $TEXT N:$NUMBER
fi
```
152. Run your script if you want to see the output. It should print one of the sentences if the random number is less than 46. It may take a couple tries. Add another  `elif`, below the last one, that uses double square brackets to check if the number variable is less than 61. If it is, use your two variables to print  `The next number is, G:<number>`

**How to change code?**

- View the  `help test`  menu to see the operators you can use with the double square brackets
- The operator you want it  `-lt`
- The condition you want is  `[[ $NUMBER -lt 61 ]]`. Don't forget the  `$`
- The statements area should look like this:  `echo $TEXT G:$NUMBER`
- This  `elif`  area should look like this:
```sh
elif [[ $NUMBER -lt 61 ]]
then
  echo $TEXT G:$NUMBER
fi
```
- The whole  `if`  statement should look like this:
```sh
if (( NUMBER <= 15 ))
then
  echo $TEXT B:$NUMBER
elif [[ $NUMBER -le 30 ]]
then
  echo $TEXT I:$NUMBER
elif (( NUMBER < 46 ))
then
  echo $TEXT N:$NUMBER
elif [[ $NUMBER -lt 61 ]]
then
  echo $TEXT G:$NUMBER
fi
```
153. One more case to handle. Add an  `else`  at the bottom of the  `if`  that uses your two variables to print  `The next number is, O:<number>`.

**How to change code?**
- View the  `if/else`  in your  `countdown.sh`  file to see how you did it before
- You don't need a condition or the  `then`  on this one
- Here's an example:
```sh
if CONDITION
then
  STATEMENTS
elif CONDITION
then
  STATEMENTS
...
else
  STATEMENTS
fi
```
- The  `else`  area should look like this:
```sh
else
  echo $TEXT O:$NUMBER
```
- The whole  `if`  should look like this:
```sh
if (( NUMBER <= 15 ))
then
  echo $TEXT B:$NUMBER
elif [[ $NUMBER -le 30 ]]
then
  echo $TEXT I:$NUMBER
elif (( NUMBER < 46 ))
then
  echo $TEXT N:$NUMBER
elif [[ $NUMBER -lt 61 ]]
then
  echo $TEXT G:$NUMBER
else
  echo $TEXT O:$NUMBER
fi
```
154. Run your script a few times and make sure it's working.

Here full source code:
```sh
#!/bin/bash

# Bingo Number Generator

echo -e "\n~~ Bingo Number Generator ~~\n"

NUMBER=$(( RANDOM % 75 + 1 ))
TEXT="The next number is, "

if (( NUMBER <= 15 ))
then
  echo $TEXT B:$NUMBER
elif [[ $NUMBER -le 30 ]]
then
  echo $TEXT I:$NUMBER
elif (( NUMBER < 46 ))
then
  echo $TEXT N:$NUMBER
elif [[ $NUMBER -lt 61 ]]
then
  echo $TEXT G:$NUMBER
else
  echo $TEXT O:$NUMBER
fi
```
# Program to tell a persons fortune
155. I think the generator is done 😄 The next project is a fortune teller. Use the `touch` command to create `fortune.sh` in the same folder as the other scripts.
156. Give your file executable permissions.
157. Add a `shebang` at the top of your new file that uses `bash` again
158. Add comment `Program to tell a persons fortune`
159. Add a title for this one like the others. This one should say `~~ Fortune Teller ~~`. Don't forget the empty line before and after it.
160. Run the file once to make sure it's working.
161. This program will have an array of responses. One will be printed randomly after a user inputs a question. Practice first 😄 In the terminal, create an array like this: `ARR=("a" "b" "c")`
162. Each variable in the array is like any other variable, just combined into a single variable. In the terminal, print the second item in the array with `echo ${ARR[1]}`. Note that the first item would be index zero. It print to b
163. If you recall, you were able to print all the arguments to your `countdown.sh` script with `echo $*`. `echo $@` would have worked as well. Similarly, you can use the `*` or `@` to print your whole array. In the terminal, use `echo` to print all the items in your array. (a b c)
164. The variable must be in that `declare` list. View your array variable using the `declare` command and the `-p` flag. (`declare -p ARR`). It prints:
```txt
declare -a ARR=([0]="a" [1]="b" [2]="c")
```
165. The `-a` next to it stands for `array`. In your script, create an array named `RESPONSES`. Give it these six values: `Yes`, `No`, `Maybe`, `Outlook good`, `Don't count on it`, and `Ask again later`.
```sh
RESPONSES=("Yes"  "No"  "Maybe"  "Outlook good"  "Don't count on it"  "Ask again later")
```
166. In your script, use `echo` to print the last item in the array.
167. Run it to see the output. (It print to ask again later)
168. You will randomly print one of the values. In your script, create a variable named `N`. Set it equal to a random number between `0` and `5`, the first and last index of the array.

**How to set?**

- Use the modulus (`%`) operator and  `6`  to get a number between  `0`  and  `5`
- Look at the random number you created in the  `bingo.sh`  file for a hint
- Here's an example:  `VARIABLE=$(( <calculation> ))`
- Calculate a random number in the range you want with  `RANDOM % 6`
- Add  `N=$(( RANDOM % 6 ))`  to the script

169. Change your `echo` command to print the item in the array whose index is the random number you generated.

**How to change your echo command?**

- Use your  `$N`  variable as the index where you print an item from the array
- Don't forget that scripts run from top to bottom, so you can't use any variables before they are created
- Change the  `echo`  line to  `echo ${RESPONSES[$N]}`

170. You will create a function to generate an answer. Check the `help` menu to see if you can find anything.
171. See any that might help? There's one that says `function`. See if you can find out more about it.
```txt
function: function name { COMMANDS ; } or name () { COMMANDS ; }
    Define shell function.
    
    Create a shell function named NAME.  When invoked as a simple command,
    NAME runs COMMANDs in the calling shell's context.  When NAME is invoked,
    the arguments are passed to the function as $1...$n, and the function's
    name is in $FUNCNAME.
    
    Exit Status:
    Returns success unless NAME is readonly.
```
172. It looks like you can create a function like this:
```sh
FUNCTION_NAME() {
  STATEMENTS
}
```
Add an empty function named  `GET_FORTUNE`  to your script. Make sure the response you are printing is the last thing in the script.

**How to create function in bash?**

- Add this to your script:
```sh
GET_FORTUNE() {}
```
- Your  `echo ${RESPONSES[$N]}`  command should be at the bottom of the file
173. In your function, use  `echo`  to print  `Ask a yes or no question:`

Your function should look like this:
```sh
GET_FORTUNE() {
  echo Ask a yes or no question:
}
```
174. Call your function by putting the name of it below where you create it. No `$` needed. Make sure the response you are printing is at the bottom of the file.

**How to call function?**

Add `GET_FORTUNE` below where you create your function to call it

175. Run your script to make sure it's working.
176. In your function after you print the sentence, use `read` to get user input into a variable named `QUESTION`.
177. In your function after you print the sentence, use  `read`  to get user input into a variable named  `QUESTION`.

** How to add?**

- Add  `read QUESTION`  to your function below the  `echo`
- Your function should look like this:
```sh
GET_FORTUNE() {
  echo Ask a yes or no question:
  read QUESTION
}
```
178. Run the script again to test it out. Enter a question when it asks.
179. I want to make sure the input is a question. You are going to add a loop that asks for input until the input ends with a question mark. View the `help` menu to see if you can find an appropriate loop.
180. View more about that `until` command. That might be the one to use here.
```txt
until: until COMMANDS; do COMMANDS; done
    Execute commands as long as a test does not succeed.
    
    Expand and execute COMMANDS as long as the final command in the
    `until' COMMANDS has an exit status which is not zero.
    
    Exit Status:
    Returns the status of the last command executed.
```
181. The  `until`  loop is very similar to the  `while`  loop you used. It will execute the loop until a condition is met. Here's an example:
```sh
until [[ CONDITION ]]
do
  STATEMENTS
done
```
Add an  `until`  loop below your function. Use the double brackets to check if  `QUESTION`  is equal to  `test?`. Move the  `GET_FORTUNE`  function call to the statements area of the loop. It should run the function until you input  `test?`  as the question.

**How to add until function?**

- View the  `help [[`  or  `help test`  menu to see if you can find the operator to use
- You want the  `==`  operator
- The condition should look like this:  `[[ $QUESTION == test? ]]`
- Your  `until`  loop should look like this:
```sh
until [[ $QUESTION == test? ]]
do
  GET_FORTUNE
done
```
182. Run the script and enter something other than `test?`. Then enter `test?` after it asks for a question the second time.
183. View that `help [[ expression ]]` menu again. You need to find out how to test if the input ends with a question mark (`?`).
```txt
[[ ... ]]: [[ expression ]]
    Execute conditional command.

    Returns a status of 0 or 1 depending on the evaluation of the conditional
    expression EXPRESSION.  Expressions are composed of the same primaries used
    by the `test' builtin, and may be combined using the following operators:

      ( EXPRESSION )    Returns the value of EXPRESSION
      ! EXPRESSION              True if EXPRESSION is false; else false
      EXPR1 && EXPR2    True if both EXPR1 and EXPR2 are true; else false
      EXPR1 || EXPR2    True if either EXPR1 or EXPR2 is true; else false

    When the `==' and `!=' operators are used, the string to the right of
    the operator is used as a pattern and pattern matching is performed.
    When the `=~' operator is used, the string to the right of the operator
    is matched as a regular expression.

    The && and || operators do not evaluate EXPR2 if EXPR1 is sufficient to
    determine the expression's value.

    Exit Status:
    0 or 1 depending on value of EXPRESSION.
```
184. Let's play with these again. You can test if two strings are the same with `==`. In the terminal, use the `[[ ... ]]; echo $?` syntax you used before to test if `hello` is equal to `hello`.

Try to type `[[ hello == hello ]]; echo $?` in the terminal and press enter. It return to 0.

185. Exit status of `0`, it was true. Using the same syntax, test if `hello` is equal to `world`.

Type `[[ hello == world ]]; echo $?` in the terminal and press enter. It return to 1.

186. False. An important operator in that menu is `=~`. It allows for pattern matching. Using the same syntax but with this operator, check if `hello` contains the pattern `el`.

Type `[[ hello =~ el ]]; echo $?` in the terminal and press enter. It return 0.

187. True. The condition was checking for `el` within the word `hello`. Using the same syntax, check if `hello world` contains the pattern `lo wor`. You will need to put them both in quotes so it recognizes the spaces.

**How to check?**

Use the `=~` operator with it. Type `[[ "hello world" =~ "lo wor" ]]; echo $?` in the terminal and press enter. It return 0.

188. Your patterns have been checking for literal matches, `el` and `lo wor`. You can use regular expression characters as well, but you can't put the pattern in quotes when you do. Using the same syntax, check if `hello world` starts with an `h` by using `^h` as the pattern.

**How to check?**

Make sure not to use quotes around the pattern when using regex characters it. Type  `[[ "hello world" =~ ^h ]]; echo $?`  in the terminal. It return 0.

189. Do it again, but use `^h.+d$` as the pattern to see if the string starts with an `h`, has at least one character after it, and ends with a `d`.

**How to check?**

Type `[[ "hello world" =~ ^h.+d$ ]]; echo $?` in the terminal. It return 0.

190. In the terminal, create a variable named `VAR` that equals `hello world`.
191. Use `echo` to print the variable you just created.
192. Using the `[[ ... ]]; echo $?` syntax, check if your variable is equal to `hello world`. It return 0.
193. Using the same syntax, check if your variable ends with `?` by using the pattern `\?$`.

**Hint**

Type `[[ $VAR =~ \?$ ]]; echo $?` in the terminal. It return to 1.

194. It doesn't end with `?`. Just to make sure I don't have the pattern wrong, check if `test?` ends with `?`.

**Hint**

Type `[[ test? =~ \?$ ]]; echo $?` in the terminal. It return to 0.

195. I think that will work. Back in your script, change the `until` condition to see if your variable ends with `?`.

**Hint**

Your condition should look like this: `[[ $QUESTION =~ \?$ ]]`

196. Run the script and input something that doesn't end with `?` the first time, then something that does the second.
197. I know that it asks the same thing if the input isn't what you want. You should let users know that it needs to end with `?`. Add an `if` condition in your **function** that checks `if [[ ! $1 ]]`. Put the existing `echo` statement in the `then` area and make sure the existing `read` is below the whole `if` condition.

**Hint**
- Here's an example:
```sh
if [[ CONDITION ]]
then
  STATEMENTS
fi

read QUESTION
```
- Your function should look like this:
```sh
function GET_FORTUNE() {
  if [[ ! $1 ]]
  then
    echo Ask a yes or no question:
  fi

  read QUESTION
}
```
198. You can pass arguments to functions like you did with your script. This condition will check if one isn't passed and print the sentence. Add an `else` to your `if`. Use `echo` to print `Try again. Make sure it ends with a question mark:` if the condition fails.

**Hint**
- Your  `if`  condition should look like this:
```sh
if [[ ! $1 ]]
then
  echo Ask a yes or no question:
else
  echo Try again. Make sure it ends with a question mark:
fi
```
199. Now, your function will print one thing if you pass it any argument, and something else if not. In the `until` loop, add `again` as an argument to where you call the function.

**Hint**

Your  `until`  loop should look like this:

```sh
until [[ $QUESTION =~ \?$ ]]
do
  GET_FORTUNE again
done
```
200. Now, each time the function is called in the `until` loop, it will pass `again` as an argument and print the `Try again...` sentence. Before your `until` loop, call the function without an argument so the first time it runs, it prints the initial sentence.

**How to add?**

Add  `GET_FORTUNE`  before the  `until`  loop

201. Run the script and enter something without a question mark when it asks the first time. Use a question mark the second time.
202. Awesome. One last thing. Add an empty line in front of where you print the response.

**Hint**

The suggested command should look like this: `echo -e "\n${RESPONSES[$N]}"`
Here full source code:
```sh
#!/bin/bash

# Program to tell a persons fortune

echo -e "\n~~ Fortune Teller ~~\n"

RESPONSES=("Yes"  "No"  "Maybe"  "Outlook good"  "Don't count on it"  "Ask again later")
N=$(( RANDOM % 6 ))

# Create a function
function GET_FORTUNE() {
  if [[ ! $1 ]]
  then
    echo Ask a yes or no question:
  else
    echo Try again. Make sure it ends with a question mark:
  fi

  read QUESTION
}

# until loop function
until [[ $QUESTION =~ \?$ ]]
do
  GET_FORTUNE again
done

echo -e "\n${RESPONSES[$N]}"
```
# Program to run my other four programs
203. Excellent. One last program to make. Use `touch` to create a new file named `five.sh` in the same folder as the others.
204. Give your file executable permissions.
205. Add a `shebang` to the new script that uses `bash` like the others.
206. Add a comment below the `shebang` that says, `Program to run my other four programs`
207. This program will run all the programs you made so far consecutively. Add the command to run the `questionnaire.sh` file.
208. Run the file to see if it works. Enter input when it asks.
209. Add commands to run the rest of your scripts in the file. They should be in this order: `questionnaire`, `countdown`, `bingo`, and `fortune`. Don't forget that your `countdown.sh` file needs an argument, so put a `3` next to it.

**Hint**: Your  `five.sh`  file should have these commands:
```sh
./questionnaire.sh
./countdown.sh 3
./bingo.sh
./fortune.sh
```
210. Okay, use `clear` to empty out what's in the terminal before the big moment.
211. Run the script and enter input when it asks.
```txt
~~ Questionnaire ~~

What's your name?
Quang Anh
Where are you from?
Vietnam
What's your favorite coding website?
F8 Fullstack

Hello Quang Anh from Vietnam. I learned that your favorite coding website is F8 Fullstack!

~~ Countdown Timer ~~

3
2
1
0

~~ Bingo Number Generator ~~

The next number is, N:32

~~ Fortune Teller ~~

Ask a yes or no question:
Are you good?

No
```
212. Cool. I think all the scripts are done. View the `help` menu again I want to explore one more thing.
213. View more about that `type` command.
214. It says you can view the type of a command with `type <command>`. Just for fun, lets take a look at the type of a few different commands. View the type of `echo`. It print to echo is a shell builtin.
215. View the type of the `read` command. It print to read is a shell builtin.
216. View the type of `if`. It print to if is a shell keyword.
217. View the type of `then`. It print to then is a shell keyword.
218. Those were all from the `help` menu and described as a `shell builtin` or `shell keyword`. View the type of `bash`. It print shebang bash is /usr/bin/bash.
219. That's the location of the `bash` command. View the type of `psql`. It print to psql is /usr/bin/psql.
220. It's showing the location of the commands. View the type of your `./five.sh` file.
221. Last step, close the terminal with the `exit` command. Thanks and happy coding!
