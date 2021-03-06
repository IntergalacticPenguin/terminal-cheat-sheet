
## What is it?
📃 **Terminal, bash syntax and command cheat sheet**<br>
🙈 I may not be an author of some of the tips<br>
⚠️ Use at your own risk<br>
😍 Feel free to **contribute via pull request**<br>
⭐️ **Hit star if you like it** and make me happy
## Basic syntax
### Command chaining
`command1; command2; command3;` - execute command regardless of sucess of the previous command<br>
`command1 && command2` - execute command2 if command1 executed successfully<br>
`command1 || command2` - execute command2 if command1 execution failed<br>
*By the UNIX convention, the exit status of 0 denotes success, and anything else denotes a failure*<br>
`command1 &` - execute command in background<br>
`wait` - wait untill all background tasks are done
### Variable comparsion
`if [ "$var" -eq 1 ]`<br>
Always use **spaces between brackets and the condition** <br>
Always **quote a tested variable**<br>

#### Integer comparison operators
**-eq** - equal to `if [ "$a" -eq "$b" ]`<br>
**-ne** - not equal to `if [ "$a" -ne "$b" ]`<br>
**-gt** - greater than if `[ "$a" -gt "$b" ]`<br>
**-ge** - greater than or equal to if `[ "$a" -ge "$b" ]`<br>
**-lt** - less than `if [ "$a" -lt "$b" ]`<br>
**-le** - less than or equal to `if [ "$a" -le "$b" ]`<br>
**\<, \<=, >, >=**  - within double parentheses `(("$a" < "$b"))`<br>

#### String comparison operators
**-n** - string is not null `if [ -n "$string" ]`<br>
**-z** - string is null, that is, has zero length `if [ -z "$string" ]`<br>
**= or ==** - equal to, `if [ "$a" = "$b" ]`<br>
**!=** - not equal to, if [ "$a" != "$b" ]<br>
The == comparison operator behaves differently within a double-brackets test than within single brackets<br>
`[[ $a == z* ]]`   - true if $a starts with an "z" (pattern matching)<br>
`[[ $a == "z*" ]]` or `[ "$a" == "z*" ]` - true if $a is equal to z* (literal matching)<br>
`[ $a == z* ]` - file globbing and word splitting take place<br>
\< - less than, in ASCII alphabetical order, if [[ "$a" < "$b" ]], if [ "$a" \< "$b" ]<br>
\> - greater than, in ASCII alphabetical order, if [[ "$a" > "$b" ]], if [ "$a" \> "$b" ]<br>
## Useful commands
### man
`man <command>` - show command manual, exit with q
### curl
`curl -o <filename> -k <url>` - download file from url
### grep
`grep <text>` - find lines containing \<text><br>
`grep ^<text>` - find \<text> at the start of a line<br>
`grep <text>$` - find \<text> at the end of a line<br>
`grep <text>.` - find line with \<text> and exactly one character immediately after it<br>
`grep <text>.?` - find line with \<text> and one optional character immediately after it<br>
`grep <text>Z+` - find line with \<text> and one or more Z characters immediately after it<br>
`grep <text>*` - find line with \<text> and any number of characters immediately after it<br>
### sort
`sort -u` - strip duplicate lines
### tr
`echo "some.string.with.dots" | tr . _` - replace dots with underscores
### awk
`cat <some-file> | awk '{print $2}'` - get second word from each line
### file
`file image_file.jpg` - file information including image resolution etc
## Oneliners
### Run remote script
`curl -L https://raw.githubusercontent.com/dummyuser/great-repo/master/install.sh | bash`
### Command result if
`[ $(id -u) -eq 0 ] && return $TRUE || return $FALSE`
### Var is number
`[ "$VAR" =~ ^[0-9]+$ ]`
### Remove suff/pre-fix
`foo=${string#"$prefix"}`<br>
`foo=${foo%"$suffix"}`<br>
### Format output into columns
`echo <tbd> | column` 
### Schedule command
`<cmd> | at <time>` - run command at scheduled time
### Remove trailing carriage return
`echo "<some-text-with-newline>" | tr -d '\r'`
### Colorized output
`tput setaf 1; echo WARNING; tput sgr0;`<br>
[Output color codes](https://unix.stackexchange.com/questions/269077/tput-setaf-color-table-how-to-determine-color-codes)<br>
## Code snippets
[Argument handling](https://github.com/IntergalacticPenguin/mobile-toolkit/blob/master/android/aoptions)
## Git
`git reset --soft` - cancel commits, keep changes<br>
`git branch -m new-name` - rename local branch<br>
`git branch -d <branch_name> - delete local branch`<br>
`git commit --amend` - add to previous commit<br>
`git remote prune origin` - remove merged branches<br>
[Conflict resolving manual](https://help.github.com/en/articles/resolving-a-merge-conflict-using-the-command-line)<br>
## Terminal shortcuts
ctrl+u - stash command<br>
ctrl+y - pop stash<br>
ctrl+l - clear<br>
