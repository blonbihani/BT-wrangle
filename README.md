# BT-wrangle
The play I'm assigned with is the world-famous Shakespear's play, [Hamlet](http://shakespeare.mit.edu/hamlet/full.html).

## Chosen Speakers
- Speaker:1 'HAMLET'
- Speaker:2 'OSRIC'

## Question: Find the combined number of times each of these speakers spoke in the entire play.

Solution: Below are the steps and techniques I used to count the number of times "HAMLET" and "OSRIC" spoke in the play HAMLET, using GitBash.

### 1) Retrieve/ fetch the entire play to a text file
``` 
curl "http://shakespeare.mit.edu/hamlet/full.html" |sed 's/<\/*[^>]*>//g' > input.txt
```

### 2) Find matches with the strings
- HAMLET
```
grep -i 'HAMLET' input.txt
grep -i '^HAMLET' input.txt
grep -i '^HAMLET$' input.txt

```
To count the occurence of the word 'HAMLET'
```
grep -i '^HAMLET$' input.txt -c

```

- OSRIC
```
grep -i 'OSRIC' input.txt
grep -i '^OSRIC' input.txt
grep -i '^OSRIC$' input.txt
```
To count the occurence of the word 'OSRIC'
```
grep -i '^OSRIC$' input.txt -c
```

### 3) Redirect the string counts to other files
```
grep -i '^HAMLET$' input.txt -c > HamletCount.txt
grep -i '^OSRIC$' input.txt -c > OsricCount.txt
```
### 4) Count the total number of times 'HAMLET' and 'OSRIC' spoke and store it in a result file
```
paste HamletCount.txt OsricCount.txt | awk '{ print $1 + $2 ;}' > result.txt
```

## Final Answer
``` cat result.txt ```

The final answer is 384.
