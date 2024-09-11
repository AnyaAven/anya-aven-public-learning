# AWS, CI/CD, and GitHub Actions

The goal of this exercise is to learn more about AWS technologies,
Continuous Integration (CI) and Continuous Deployment/Delivery (CD).

## Workflow

---
For example, we have a repo of 4 contributors.
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

### Advantages of GitHub Actions

- Same tool as our code repository.
- Integrations are great!

> "install java, install docker, etc", -> "Create an environment with..."

Can also use workflow templates too! Provided by GitHub.

## Syntax of a workflow file

`name` (optional) - Name of workflow
```yml
name: Java CI Workflow
```

`on` (required) - name of GitHub event

```yaml
on: # GitHub event
    push: 
        branches: [master] 
        # Every time someone 
        # on this repo pushes to master branch,
        # we trigger this workflow
    pull_request:
        branches: [master]
```

- `jobs` (required) - Sequence of tasks (Each job name is user defined)
- `actions/` - This is where GitHub stores predefined actions. 
Check it out yourself at [github/actions](https://github.com/actions)
- `checkout@v2` - this is a common action and is provided by GitHub
- Predefined actions can be used with `uses` attribute.
```yml
jobs: 
  build:
    runs_on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      
      - name: Set up JDK 1.8
        uses: actions/setup-java@v1 # No need to install JAVA 1.8 yourself! Predefined
        with: 
          java-version: 1.8 
```

Now it is important to know what we will be running, continue this inside of steps
```yml
# ... previous steps
- name: Grant execute permission for gradlew
  run: chmod +x gradlew # run this command

- name: Build with Gradle
  run: ./gradlew build # run this command next
```

## Running a GitHub action
1: Put your yml file in `my-project/.github/workflows/action-name.yml`.
2: Activate your specific event, in this case we can do a Pull Request.
3: All done! Check out the progress of your action under the `Details` link

---
### Where does this code run?
GitHub actions is managed by GitHub! Each job in a workflow 
runs in a fresh virtual environment 

## Additional jobs
- `publish` - After running our first job, on publish it will run.

## Skipping Workflow runs

Workflows that would otherwise be triggered using on: push or on: pull_request won't be triggered if you add any of the following strings to the commit message in a push, or the HEAD commit of a pull request:

* `[skip ci]`
* `[ci skip]`
* `[no ci]`
* `[skip actions]`
* `[actions skip]`

[Docs](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/skipping-workflow-runs)