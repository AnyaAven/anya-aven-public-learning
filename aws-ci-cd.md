The goal of this exercise is to learn more about AWS technologies,
Continuous Integration (CI) and Continuous Deployment/Delivery (CD).

Workflow
For example we have a repo of 4 contributors.
When someone finds a bug, an issue is created.
That issue is either assigned to themselves or another contributor.
That issue is fixed and PR is made to merge into the master branch.
When merging, check if all tests pasts (CI) and run deployment operations.
Prepare release notes and update version number.

GitHub actions helps automate the workflow
A GitHub event is "when something happens IN or TO your repo"
PR created, contributor joins, issue created, PR merged, etc.

Example:
Listen for an event, -> action
label, -> action
assign, -> action
reproduce(add comments) -> action

The chain of actions above would make up a workflow

Advantages of GitHub Actions
Same tool as our code repository.
Integrations are great!
- "install java, install docker, etc", -> "Create an environment with..."

Can also use workflow templates too!

