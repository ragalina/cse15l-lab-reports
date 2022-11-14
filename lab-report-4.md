## Vim
1. [Changing Variable Names with Vim](#changing-variable-names-with-vim)
2. [Vim v. VS Code](#vim-v-vs-code)

## Changing Variable Names with Vim
We had the following task: 
- In DocSearchServer.java, change the name of the ```start``` parameter of getFiles, and all of its uses, to instead be called ```base```.

This was our shortest solution: 
```/``` ```start``` ```<enter>``` ```c``` ```e``` ```base``` ```<esc>``` ```n``` ```.``` ```n``` ```.``` ```n``` ```.``` ```:``` ```w``` ```q``` ```<enter>```

After ```/``` ```start```, the cursor moves to the first instance of ```start```.

![first](/lab-report-4/4-:start.png)

After typing ```c``` ```e```, we enter insert mode.

![second](/lab-report-4/4-ce.png)

Next, we change the first instance of ```start``` to ```base```.

![third](/lab-report-4/4-base.png)

Then, we use ```<esc>``` to exit insert mode and use ```n``` ```.``` to change the next instance of start.

![fourth](/lab-report-4/4-n..png)

Finally, we use ```:wq``` to save our changes.

![fifth](/lab-report-4/4-save.png)

## Vim v. VS Code

Making the variable name change from ```start``` to ```base``` took 44 seconds with VS Code and scp'ing to the remote system. To finish the task in this time, I had to prepare the scp command so I could access it with the up arrow, which isn't too practical in day-to-day work. 

It took me 44 seconds with vim as well. Vim used fewer key strokes and was, overall, much simpler. I belive I could significantly shorten the time it took with Vim once I become more comfortable with the commands.

Q. Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

- I would prefer using Vim, since it would involve less scp'ing files and logging into the remote system, both of which are lengthy commands.

Q. What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

- If the project was writing a lot of code, I might prefer VS Code since I like the overall interface more. Additionally, for changing variable names, I could simply use VS Code's refactoring capabilities. For making many small edits to the code, I think Vim would be easier. 