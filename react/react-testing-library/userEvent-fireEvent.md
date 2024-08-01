## userEvent() vs fireEvent()

Behind the scenes, userEvent uses the fireEvent. 
You can consider fireEvent being the low-level api, while userEvent sets a flow of actions.

`userEvent` has visibility and intractability checks, e.g., users can't interact 
with disabled or hidden elements.

`fireEvent` exists for a reason and there are valid cases to use it.
It should be used _sparsely_, think of it as an escape hatch.

### Resources
[docs](https://testing-library.com/docs/user-event/intro/#difference-to-fireevent)
[Why you should use it](https://ph-fritsche.github.io/blog/post/why-userevent)
