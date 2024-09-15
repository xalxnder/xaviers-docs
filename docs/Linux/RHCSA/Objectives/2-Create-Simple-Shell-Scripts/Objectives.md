### Conditionally execute code (use of: if, test, [], etc.)
```bash
#!/bin/bash  
echo "Enter a number"  
read n  
if [ $n -lt 100 ]; then  
printf "$n is less than 100\n"  
fi
```




### Use Looping constructs (for, etc.) to process file, command line input

```bash
#!/bin/bash

for i in 1 2 3 4 5
do
   echo "Welcome $i times"
done
```

### Process script inputs ($1, $2, etc.)
	- Inputs are stored as $1,$2, etc.
	- If you want to see all of them, use $@
-   Processing output of shell commands within a script

>[!TIP] Use `bash -x` to enter debug mode.

# Example Scripts

```bash
#Countdown script that converts the input to seconds, then counts down.
#!/bin/bash

if test -z $1
then
        echo provide number of minutes
        read COUNTER
else
        COUNTER=$1
fi

COUNTER=$(( COUNTER * 60 ))

while [ $COUNTER -gt 0 ]
do
        echo $COUNTER seconds remaining
        COUNTER=$(( COUNTER - 1 ))
        sleep 1
done

echo break is over, continuing
```