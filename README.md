# learning-sed-grep-awk

## grep
Grep is a command line tool used for searching for text matching a query in a document. The basic syntax is:
bash```
grep <searchQuery> <fileToSearch>
```
For example:
bash```
grep biology romad_and_mimi_story.txt
```
will return the lines in romad_and_mimi_story.txt that contain the word biology.

But what if we use:
bash```
grep Biology romad_and_mimi_story.txt
```
We get nothing! Why is that? Well, grep is normally case-sensitive unless you tell it to ignore case. To ignore case, we can use the -i flag.
bash```
grep -i Biology romad_and_mimi_story.txt
```
gives us the same output as the first commmand!

To find lines that DO NOT contain a given word, we use the -v (invert match) flag. So, if we wanted to find all lines within the story that did not contain the word "Mimi", we would use
bash```
grep -v Mimi romad_and_mimi_story.txt
```

We can also use the -q flag to 

