# learning-sed-grep-awk

## grep
Grep is a command line tool used for searching for text matching a query in a document. The basic syntax is:
```bash
grep <searchQuery> <fileToSearch>
```
For example:
```bash
grep biology cat_stories/romad_and_mimi_story.txt
```
will return the lines in romad_and_mimi_story.txt that contain the word biology.

But what if we use:
```bash
grep Biology cat_stories/romad_and_mimi_story.txt
```
We get nothing! Why is that? Well, grep is normally case-sensitive unless you tell it to ignore case. To ignore case, we can use the -i flag.
```bash
grep -i Biology cat_stories/romad_and_mimi_story.txt
```
gives us the same output as the first commmand!

To find lines that DO NOT contain a given word, we use the -v (invert match) flag. So, if we wanted to find all lines within the story that did not contain the word "Mimi", we would use
```bash
grep -v Mimi cat_stories/romad_and_mimi_story.txt
```

We can also use the -q flag to silence grep, but output the result to the shell as a return value. If the result is 0, the query was found. If not, the result is one.
```bash
grep -q biology cat_stories/romad_and_mimi_story.txt
```
```bash
echo $?
```
The above commands should return 0, as the word biology is in this txt file!

```bash
grep -q helloworld cat_stories/romad_and_mimi_story.txt
```
```bash
echo $?
```
You should get 1 here, since helloworld is not contained in this txt file.

Neat! So we've learned how to look through one file! But what if we want to recursively search through directories and subdirectories? For that, we'll use the -r flag.
```bash
grep -r -i genetic cat_stories
```
You should see a few results here! As we can see, this allows us to look through folders within a directory.

If you'll notice, one of the last results returned a line that used "genetically". What if we wanted to only match the word "genetic" (without including results that have words that include "genetic")? For that, we use the -w flag!
```bash
grep -w -i -r genetic cat_stories
```

Finally, what if we are interested in multiple seach terms? We can use the -E (extended regexp) flag with the syntax below:
```bash
grep -E "<query1>|<query2>..." <fileName>
```

Let's try this out by expanding on our previous search. Notice we use the -E option in combination with -i (to ignore case) and -r (to recursively search through the directory). We are also looking for 3 search terms ("biology" OR "genetic" OR "neural networks").
```bash
grep -E -i -r "biology|genetic|neural networks" cat_stories
```

###### Test Yourself!
How many bits of information does a DNA nucleotide contain?
Who hosts the Talking Biotech podcast?

The answers are hidden within the cat_stories directory. Are you able to find them using one grep command?



