# What To Look For in a Code Review

## Architecture/Design

### Single Responsibility Principle:
- The idea that a method should have one-and-only-one responsibility. Should be applied to classes too.
- If we have to use "and" to describe a method it might be at the wrong level of abstraction.

### Code Duplication:
- Apply the 3 strikes rule.
- If code is copied once it's usually ok, although not great. If it's copied again, it should be refactored to have the common functionality split out.

### Leave it better than you found it:
- If changing a messy area of code it's tempting to add a few lines and leave.
- Try to go one step further and leave it nicer than you found it.

### Potential Bugs:
- Off-by-one errors?
- Will it terminate how we expect?

### Error Handling:
- Null handling?
- Are errors handled explicitly where necessary?

### Efficiency:
- If there is an algorithm in the code, is it using an efficient implementation?

## Style

### Method Names:
 - If a method is named `getMessageQueueName` and it is actually doing something entirely different like altering the queue positions then it's a misleading function and should be renamed.

### Variable Names:
- Be as verbose as you need.
- Expressive variable names make it easier to understand code when we revisit it later.

### Function Length:
- If a function is greater than 50 lines, it should probably be cut into smaller pieces.

### Class Length:
- If a class is greater than 300 lines, it should probably be split into separate objects.

### Commented Code:
- Remove it.

### Method Arguments:
- Sometimes it can't be helped, but if a method has more than 3 parameters it's a sign it could be grouped in a different way.

### Readability:
- Is it easy to understand? Do I have to pause frequently to decipher it?