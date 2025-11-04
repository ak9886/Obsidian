---
updated_at: 2025-09-17T19:42:29.126+05:30
edited_seconds: 10
---
# Linux Commands – Simple Notes

Think of **Linux** like a toy box. Commands are like magic spells you say, and the computer listens. Each spell makes something happen.

---

## a) Basics
1. `echo SRM` → Computer repeats “SRM”.
2. `clear` → Wipes the screen like a chalkboard.
3. `date` → Shows today’s date and time.
4. `cal 2003` → Calendar for the year 2003.
5. `cal 6 2003` → Calendar for June 2003.
6. `passwd` → Change your secret password.

---

## b) Working with Files
- `ls` → Show files in the folder.
- `ls -l` → Show files with details (size, date, owner).
- `ls -a` → Show hidden files too.

- `cat > f1` → Make a new file *f1* and type inside it.
- `cat f1` → Read the file out loud.

- `wc f1` → Count letters, words, and lines in *f1*.
- `wc -c f1` → Only letters.
- `wc -w f1` → Only words.
- `wc -l f1` → Only lines.

- `cp f1 f2` → Copy *f1* into *f2*.
- `mv f1 f2` → Rename *f1* to *f2*.
- `rm f1` → Delete *f1*.
- `head -5 f1` → Show first 5 lines.
- `tail -5 f1` → Show last 5 lines.

---

## c) Working with Directories (Folders)
- `mkdir elias` → Make new folder *elias*.
- `cd elias` → Go inside the folder.
- `rmdir elias` → Remove empty folder.
- `pwd` → Where am I right now?
- `cd` → Go home.
- `cd ..` → Go one step up.
- `cd -` → Go back to last place.
- `cd /` → Go to the top folder.

---

## d) File Name Tricks
- `ls f?` → Files starting with *f* + one more letter.
- `ls *.c` → Files ending in `.c`.
- `ls [gpy]et` → Matches *get, pet, yet*.
- `ls [a-d,l-m]ring` → Matches *aring, bring, dring, lring, mring*.

---

## e) Redirection
- Input `<` → Give a file to a command.  
  Example: `wc -l < ex1`
- Output `>` → Save command’s result into a file.  
  Example: `who > f2`
- Append `>>` → Add to a file.  
  Example: `cat >> f1`

---

## f) Piping (|)
Connect commands like Lego blocks.

- `cat f1 | more` → Show file slowly, page by page.
- `head -6 f1 | tail -2` → Show 5th and 6th lines.

---

## g) Environment Variables
- `echo $HOME` → Home folder.
- `echo $PS1` → Prompt symbol.
- `echo $PS2` → Continuation symbol.
- `echo $LOGNAME` → Your login name.
- `echo $PATH` → Where Linux looks for programs.

---

## h) File Permissions
Files are like locked doors.

- `chmod ug+rw f1` → Give user & group read/write access.

Numbers:  
- 7 = read + write + run  
- 5 = read + run  
- 4 = read  

Example: `chmod 754 f1`  
- User = 7 → read/write/run  
- Group = 5 → read/run  
- Others = 4 → read  

---

## i) Filters
Filters clean or pick parts of files.

- `cat f1` → Show file.
- `head -5 f1` → First 5 lines.
- `tail -10 f1` → Last 10 lines.
- `cut -c 3-5 f1` → Show only characters 3 to 5.
- `cut -d"," -f1,3 f1` → Show 1st & 3rd parts separated by commas.
- `sort f1` → Sort lines.
- `sort -r f1` → Sort in reverse.
- `uniq f1` → Remove duplicates (must be sorted first).
- `tr '[a-z]' '[A-Z]' < f1` → Make text uppercase.

---

## j) Admin Commands
- `who` → Who’s logged in.
- `who am i` → Show your details.
- `tty` → Which terminal you’re on.
- `uname` → Show system name.
- `uname -a` → Show all system details.
- `id` → Show user ID info.
- `df` → Disk usage.
- `du` → Disk space taken by files.

---

## k) Shell Programs
Small programs to automate tasks.

### Example 1: Print 1 to n
```sh
echo "Enter n"
read n
i=1
while [ $i -le $n ]
do
  echo $i
  i=`expr $i + 1`
done
```

### Example 2: Factorial of n
```sh
echo "Enter n"
read n
f=1
while [ $n -ge 1 ]
do
  f=`expr $f \* $n`
  n=`expr $n - 1`
done
echo "Factorial is $f"
```

### Example 3: Fibonacci Series
```sh
echo "Enter n"
read n
a=0
b=1
echo $a
echo $b
i=2
while [ $i -lt $n ]
do
  c=`expr $a + $b`
  echo $c
  a=$b
  b=$c
  i=`expr $i + 1`
done
```

### Example 4: Reverse a Number
```sh
echo "Enter n"
read n
rev=0
while [ $n -gt 0 ]
do
  r=`expr $n % 10`
  rev=`expr $rev \* 10 + $r`
  n=`expr $n / 10`
done
echo "Reverse is $rev"
```

### Example 5: Check Palindrome Number
```sh
echo "Enter n"
read n
num=$n
rev=0
while [ $n -gt 0 ]
do
  r=`expr $n % 10`
  rev=`expr $rev \* 10 + $r`
  n=`expr $n / 10`
done
if [ $rev -eq $num ]
then
  echo "Palindrome"
else
  echo "Not Palindrome"
fi
```

---

