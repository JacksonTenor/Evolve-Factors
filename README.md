##Problem
I chose to attempt to evolve a program that returns the number of factors a number has. I thought this would be an interesting problem as it pretty fundamentally requires looping, but is still a fairly simple problem that someone might be given in an intro to programming course. 

##Functions
For the functions and stacks I gave the program I used everything in the base propel library aside from the string stack and associated functions. I figured that for this problem if it ever touched a string it was already lost, and it was better to avoid that. I additionally had to add additional functionality. I needed looping, so I added a exec_for method. It used an additional stack, the control stack, which held what was essentially the variable iterating to create the loop. Finally, I added an int_to_control function to, well, move an integer to the control stack. This would set up loops. In hindsight, I think a read_control function would have helped, as human programmers often use the number of iterations through a loop to mean something. Allowing the program similar functionality might have helped, but I don’t think it’s the only thing needed.

##Tests / Error/ Selection
The test set is the numbers 1-50. The error is the absolute value of the difference between the top value in the integer stack and the expected value, or 100 if the stack is empty. I used lexicase selection because it seems pretty darn good at doing things well.

##Slight changes for hopefully better luck (did not work)
To increase my chances of a lucky jump to for loop magic happening, I increased the population size to 1000 and allowed for larger programs to be fully executed before stopping. This might have helped, but it did not help enough. It did, however, increase the runtime per generation significantly.

##Results
As of 351 generations (Tuesday around noon), my total best program had an error of 46 on the first 50 integers. As of 906 generations (Wednesday at 3pm), the best program has not improved from a total error of 46. This means on average it is off by under 1, but it still isn’t very impressive. The program seems to have memorized the solutions to the first 8 integers and found a pattern of repeating 2s and 4s, eventually switching to 2s and 6s, to be effective enough. (Also one 5 in there?) I think the reason this program never found a solution is because there is no reasonable path from the guessing / repeating patterns style that works well enough as a starting point to the looping necessary for truly solving the problem. 

When talking to Nic earlier I had mentioned using a map or reduce function rather than a for loop. This would have been interesting, taking the entire integer stack and mapping them to booleans, for instance. These non-looping options likely came to mind due to my work in clojure in this class. I am interested to see if those functions would have helped the program evolve a solution faster as it would take fewer lines of code being repeated or mapped, and therefore less of a ‘magic jump’ than required to switch than the for loop.
