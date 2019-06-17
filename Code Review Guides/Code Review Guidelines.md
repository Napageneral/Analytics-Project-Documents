# Code Review Guidelines

### Avoid separating code ownership:
Don't assign ownership of the code with terms like "your code" and "my code". Doing so makes code reviews feel more like a personal judgement when in reality we all share ownership of the code in the system.

### Assume best intent, stay positive:
Avoid sarcasm and negative descriptors that may be misread

### Avoid demands, offer suggestions instead:

- "What about moving this into its own method?"
- Its helpful to phrase these as questions as often times the reviewer may be missing context on why particular suggestions will not work.

### Authors should respond to suggestions:
- "Great catch, I'll update it in the next version."
- "Went ahead with the original approach due to time constraints."

### Be explicit:
Let's make **X** change because of reason **Y**

### Say if something is optional or blocking:
- "Due to security concerns we should update this method before shipping."
- "This is optional, but I think it reads better if we move this to into its own method."

### If something is confusing, ask:
- "What's the reason behind these changes?"
- "I don't understand whats happening here, could you explain?"

### Let the author know when you appreciate a change

### Explain next steps or complete the review

# Preparing Your Push To Be Reviewed

### Explain why:
- Assume readers have little or no context when reading the changes.
- Explain why we need it and what it does.

### Keep changes small:
- Large changes are difficult to review and understand.

### Note weird things:
- Explain any odd code work-arounds or buggy behavior.
