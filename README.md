# shell-script-reference

## Bash Interpreter | Executing Scripts

Bash interpreter location:

```
which bash
```

Execute with interpreter:

```shell script
bash <filename>
sh <filename>
```

Execute file directly:

- Take ownership of file

```
chmod +x <filename>
```

- Add interpreter location to the top of the script

```shell script
#!/bin/bash

# Note: You may also see #!/usr/bin/env bash instead, which can be used if you don't know the exact path for bash.

#!/usr/bin/env
```

- Execute file directly

```shell script
./<filename>
```

## Globals

Get current user

```shell script
echo "Hello, ${whoami}"
```

## Strings

Simple string does not require quotes

```shell script
echo This is a string
```

Single or double quotes requires escaping

```shell script
echo I\'m a string
```

Usage of single or double quotes requires wrapping

```shell script
echo 'Single "quotes"'
echo "Double 'quotes'"
```

Escape flag

```shell script
echo -e "Add a new line\n"
printf "Add a new line\n"
```

## Variables

Declare and use variables

```shell script
world="World"

echo "Hello, $world" # Hello, World
echo "Hello, ${world}" # Hello, World
```

> No space allowed between `=` operator

## Input

Read user input

```shell script
echo "What is your name?"

read myName

echo "My name is $myName"
```

## Conditions

if / else

```shell script
echo "What is your age?"

read age

if [$age -gt 17]
then
    echo "I am an adult"
else
    echo "I am not an adult"
fi
```

## Loops

Loop through files

```shell script
files=/folder/dir/*

for file in $files
do
    echo $(basename $file)
done
```

## Arrays

Get value from index

```shell script
array=('Value' 'Value2' 'Value3')
echo ${array[1]} # Value2
```

## Select Construct

Example

```shell script
select ITEM in [LIST]
do
  [COMMANDS]
done
```

Select an item

```shell script
PS3="Enter a number: "
select character in Sheldon Leonard Penny Howard Raj
do
    echo "Selected character: $character"
    echo "Selected number: $REPLY"
done

# 1) Sheldon
# 2) Leonard
# 3) Penny
# 4) Howard
# 5) Raj
# Enter a number: 3
# Selected character: Penny
# Selected number: 3
# Enter a number:

PS3="Enter a number: "
characters=("Sheldon" "Leonard" "Penny")
select character in "${characters[@]}"
do
    case $character in
        "Sheldon")
            echo $character # Sheldon
            ;;
        "Leonard")
            echo $character # Leonard
            ;;
        "Penny")
           echo $character # Penny
            ;;
        "Quit")
            break
            ;;
        *) echo "invalid option $REPLY";; # number chosen
    esac
done
```
