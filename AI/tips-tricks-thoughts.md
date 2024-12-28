# AI - Tips, Tricks, and Thoughts

IDEs: Cursor, Windsurf

Devin Code agent
PRs and Bug / Testing

### What model should I use?
We should know what is through put, latency, etc.
What model is best for your question?
Claude, ChatGPT, Gemini all have their own quirks. Learning more about what model is best for what would be good.


## Good Practices for Prompting
### What are the good prompting practices?
How do you separate text, and bullet points, etc.
Retrieval, drop

Figuring out these technical words and what they correspond to what be good.

## [Anthrop\c](https://www.anthropic.com/)
Helpful for prompt engineering. Using anthropic helps take your small prompt and expand it 
with best practices.

### Why won't my model change its answer?

The deeper the context the more memory is used and performance degrades.
This is something the AI space hasn't really been able to fix.

The context window is how much it can fit in it's memory.
The higher the context window's number, the bigger the context rabbit hole it can go.

**How do I get around that?**
Best tip is to switch sessions.
Prompt your current session to make a short summary of the conversation and move that
to prompt the next session, then continue.

## Pros and Cons to AI and software
Cons
- If it is solving it for you, it might be trickier to debug since it is a differnet solution

