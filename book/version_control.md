# Version control

In this chapter, we primarily discuss the benefits of using the [Git](https://git-scm.com/) version control system.

## Why do we need version control?

Manually versioning files is not appropriate or sufficient for development at pace or with input from multiple individuals.

Without automated version control, we commonly see:
* Multiple copies of files or the entire project
* Issues in resolving multiple changes to the same file
* Duplicated effort
* Difficulty understanding where changes have been made and by whom
* Difficulty understanding the order that changes have occurred in
* Difficulty identifying changes that have introduced errors
* Problems in trying to roll back changes to get code working again quickly

```{figure} https://imgs.xkcd.com/comics/documents.png
---
width: 30%
name: file_names
alt: Comic demonstrating poor file naming, like "Untitled 138 Copy.docx".
---
Documents, from [xkcd](https://xkcd.com/1459/)
```

As discussed in [](principles.md), an audit trail is essential for quality analysis.

It's important for us to be able to answer the following questions about our analysis:
* What changes have been made to our project?
* When were those changes made?
* Why were those changes made?
* Who made those changes?

Version control software, like Git, records the answers to these questions throughout the development of a project.
Using a remote Git repository maintains a single source of truth, despite multiple individuals working on a project.
It helps us to record and combine changes from multiple developers.
When used effectively, it also allows us to more easily identify changes that have negatively impacted our work and remove them.
Most importantly, it allows us to refer to specific versions of our code that have been used to produce specific outputs.


## What should I version control?

Ideally, you should include any code that is required to run your system.
In a public repository, you may need to omit confidential or sensitive code.

```{caution}

You should **not** include the following in your code repository:
* passwords, credentials or keys
* configuration files that are environment-dependent
* code that contains sensitive information
  * for example, code that describes a method for fraud detection
  * or code that contains references to personally identifiable data
  * or code that might compromise security protocols
* data, except for small example datasets
```

You might include example configuration files, or documentation describing how configuration is applied.
However, the exact configuration of a system for a particular run of your code should be recorded by logging for reproducibility purposes.

The data we use for analysis is often unreleased or sensitive.  
Unpublished, sensitive or disclosive data should never be shared in a code repository.  
As a rule of thumb, only small example datasets should be included.
It is still important to version the data that we use for our analyses, but this can be done more appropriately using databases.


## Git

Git is a distributed version control system. 
All users have access to a complete and self-contained history of changes to a given project.
It can be used to record local changes, with the option of then synchronising these changes with a central, remote repository.

The following sections describe useful concepts for using Git to version control your projects.
We use examples of Git commands throughout, but do not provide detailed descriptions of Git usage.
If you're not yet familiar with using Git, you should first look into introductory training.

```{admonition} Pre-requisites
:class: admonition-learning

Git is most commonly used via a command line interface.
In most cases this is the Windows command prompt or the UNIX bash terminal.
You should first learn command line basics through one of these resources:
* Windows and UNIX [Command Line Basics](https://learninghub.ons.gov.uk/enrol/index.php?id=534) (government analysts only)
* [Learn enough (UNIX) command line to be dangerous](https://www.learnenough.com/command-line-tutorial/basics)
* [The UNIX workbench](https://seankross.com/the-unix-workbench/)

Following this, useful training resources for learning Git include:
* [Intro to Git](https://learninghub.ons.gov.uk/course/view.php?id=532) (government analysts only)
* The [Pro Git book](https://git-scm.com/book/en/v2) - starting with Git Basics
* Software Carpentry [Version Control with Git](https://swcarpentry.github.io/git-novice/) - an applied project
* Interactive online training with [Katacoda](https://www.katacoda.com/courses/git) or [Learn Git Branching](https://learngitbranching.js.org/)
```


### Excluding information from Git repositories


#### .gitignore

As mentioned above, you may not want to include all of the files associated with your project in a Git repository.
A `.gitignore` file allows you to exclude folders or files from being tracked by Git.
Within this file, you provide a list of text patterns.
If a folder matches one of your `.gitignore` file patterns, none of the files or folder below that folder will be tracked.
If an individual file matches one of the patterns, this file will not be tracked.

Given this example `.gitignore` file:

```
secrets.yaml
sandpit/
*.csv
```

The first pattern tells Git to ignore any file with the exact name `secrets.yaml`.
The second will ignore all files within a folder named `sandpit/`.
Note that if there are multiple folders in the project named `sandpit/`, they will all be excluded.
You should make the pattern more specific if you want to exclude particular directories.
The third pattern will exclude all `.csv` files, regardless of which folder or sub-folder they are in.

```{caution}
Files that are already being tracked by Git will not be excluded when you add new patterns to your `.gitignore` file.
Ensure that you set up your `.gitignore` before adding files to be tracked in your repository.
```

Please see the [Git documentation for `.gitignore`](https://git-scm.com/docs/gitignore) for more details.


#### .Rdata files


#### Notebooks


#### Handling a data breach



### Git Commands

Git commands are run from the terminal, which is typically [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) or a command prompt.

Commands have a very standard structure in Git, namely they always starts with `git` to run the command using the Git program.

Git commands are also made up of:
* a command name, which always follows `git` (e.g. `git status`)
* command arguments, which follow the command and can be put before or after any flags (e.g. `git clone https://github.com/pandas-dev/pandas.git`)
* optional flags
  * these can be long, starting with two dashes (e.g. `--no-edit`)
  * or short, starting with one dash (e.g. `-m`)
  *  note that the `-h` flag can be used to get help for any command
* flag arguments, which follow some flags that take arguments (e.g. `git commit -m "my message"`)

You can use this [cheat-sheet](https://education.github.com/git-cheat-sheet-education.pdf) as a reference for the most common Git commands.


### Git versioning concepts

A repository (often shortened to repo) is a collection files that are being versioned by Git.
A repository is created by `init`ialising a new repo or `clone`ing an existing one.
A local repository is your self-contained copy of the project.
A remote repository is a centralised copy of a project that is often used as the truth.

A `.gitignore` file tells git not to version specific patterns of file names.
This is useful for ensuring that specific files or types are not included. For example, configuration files or data.

Commits are collections of changes to one or more files.
Every commit is attributed to the author of these changes.
Each commit has a unique hash - or identifier - associated with it, which has a long (e.g. `121b5b4f18231e4ee32c9c61f6754429f9572743`) and short version (e.g. `121b5b4`).
Every commit also has an associated message that is used to describe the changes - this is a key part of your code's audit trail.

Most commit messages are short and informative, but in some cases you may want to provide more detail.
See this model commit message from [A note about Git commit messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html):

```{code-block} text
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```

Branches are independent copies of a project's history, copied from the state of the parent branch at a specific point in that branches history.
They help to support multiple changes to a project that are developed in parallel.
The `master` is the default name for the original branch of a repository, however, some platforms are changing this default to `main`.

`HEAD` refers to the current state of the current branch.
It usually indicates the last commit that was created or checked out.
It becomes "detached" if an individual commit or a remote branch is checked out without creating a new local branch.
`HEAD` and other references are described in more detail in [References section of the Git book](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

Merge is the process of recreating changes from one branch on another branch. 
It can be done using a few different methods, including fast-forward and rebasing.

Conflicts arise when multiple changes have been made to the same part of a file.
You must indicate which change (or combination of changes) should be retained.

Don't panic!
It's easy to make mistakes, but thankfully Git's audit trail means that we can always revert back to working versions.
For most issues, [stackoverflow](https://stackoverflow.com/) is your friend.

Don't change published (i.e. `remote`) history, otherwise you might need to panic.
This causes issues across different users of the repo, as other developer's local copies may no longer contain the same history.
You must consider this before force pushing changes to a remote repository.
Create new commits that resolve or `revert` to fix the problem.


### Releases (tagging)

Regularly `commit`ing changes using Git helps us to create a thorough audit trail of changes to our project.
However, there may be discrete points in the history of the project that we want to mark for easy future reference.
Let's face it, hashes like `121b5b4` don't exactly roll off of the tongue.

Tags can be created in Git, to reference a specific point in the projects history.
A tag essentially acts as an alias for a commit hash.
You might use tags, for example, to mark a particular model version or a new software version to be released.
By default, tags will reference the current position in history (i.e. the latest commit or `HEAD`).

An annotated tag might be created for a new software version like so:

```{code-block}
git tag -a v0.2.7 -m "Release version 0.2.7"
git push origin v0.2.7
```

You can also retrospectively tag an older commit, by providing that `commit`'s hash:

```{code-block}
git tag -a v0.1.0 -m "Release version 0.2.7" 9fceb02
git push origin v0.1.0
```

Once tags have been created, these locations in the projects history can be easily recovered by either checking out:

```{code-block}
git fetch --all
git checkout tags/v0.1.0 -b new_branch_name
```

or cloning the tag:

```{code-block}
git clone https://github.com/<user>/<repo>.git --branch=v0.1.0
```

## Beyond Git - GitHub

A number of platforms extend the functionality of Git, to further improve collaborative working.

Here we describe some of the beneficial features supported by GitHub, the world's leading software development platform.
GitHub provides additional tools for collaborative workflows, including:
* Access management for viewing and contributing
* Issues
* Project boards
* Forking
* Pull requests
* Continuous Integration

Many of these project management tools are also discussed on the [GitHub features page](https://github.com/features/project-management/).


### Access management

GitHub repositories have a [visibility setting](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/setting-repository-visibility) that represents whether the repo can be viewed publicly or only by owners of the project,
Note that some GitHub features are limited or are not available for private repos on free GitHub accounts.

Organizations provide an area for collating multiple repos that are associated with a particular team or department.
Within Organizations, Teams can be also created to manage view and contribution permissions for projects within the Organization.
External collaborators can also be added to projects, to allow direct contribution from those outside of the Organization.

Despite the visibility status of a repo, only Organization members and collaborators may make direct contributions to the code in the repo.
Others can contribute by Pull Request.

Detailed setup and management of Organizations and Teams are described in the [relevant section of the GitHub Docs](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-organizations-and-teams).


### Forking

Forking a repo takes a complete copy of a project's current state, including all existing branches and tags.
You can then make modifications on this copy, without affecting the original repo.

You might want to do this because you:
* Would like to contribute to a repository, but are not added to the repo as a collaborator
* Would like to make changes to the project for your own use

Note that forks do not automatically synchronise with the original repo.
This means that changes to the original repo after you create a fork need to be manually synchronised if you want to include them in your repo.
When you would like to offer to contribute your changes to the project (see Pull requests below), you should ensure that you synchronise your branch with any new changes first.

See the GitHub Docs for [instructions on forking a repo and keeping your fork up to date](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/fork-a-repo) with the project and also [working with forks](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/working-with-forks).


### Issues

Issues offer a method for requesting or recording tasks, including enhancements and bug fixes in your project.
They act as a collaborative todo list, which users can easily contribute to.

The basic elements of an issue are the:
* Title and description, provided by the person that submitted the issue
* Labels to categorise issues (e.g. bug)
* Comments, where others can discuss the issue
* Assignees that are working on resolving the issue

Issues can be linked to specific Pull Requests (below) that resolve or help to solve the issue.
They can also reference other related issues (e.g. `#12`), both within the repo and between repos.

Issues are useful for discussing bugs and new features within the team, but can also be added by users.
This is often the case with open source projects, providing users with a platform to highlight what would be most useful for them.

[Setting issue templates](https://docs.github.com/en/free-pro-team@latest/github/building-a-strong-community/configuring-issue-templates-for-your-repository) for your project can be an effective way of encouraging collaborators to use informative descriptions.
For example, a bug issue should include simple instructions to help maintainers reproduce the problem.
While feature requests might include information on how the user expects the new feature to work or details what problem it will help them to overcome.

Issues are a useful soundboard for requesting changes, but the implementation of changes are handled by Pull Requests (below).


### Pull requests

A pull request lets you describe changes that you have made to a repo.
The request is based on the difference between a target branch (usually `dev` or `master`) and a source branch, where you have implemented changes.
The source branch can the in the same repository, or might be in a Fork (below) of the repository if you are not a member of the project.

Pull requests create an interface for discussion and review of your changes.
Once a project maintainer is happy with your changes, they can merge them onto the target branch.
After merging, pull requests preserve a record of the changes and associated discussion.

You can label pull requests a draft to indicate they are still a work in progress.
This prevents them from being merged prematurely.
This can be useful when you would like to request advice or early feedback on the changes you are making.

Like issues, pull requests can have assignees that are working on them.
You can also assign reviewers and tag (`@`) project collaborators as part of the discussion.


### Project boards

[Project boards](https://docs.github.com/en/free-pro-team@latest/github/managing-your-work-on-github/about-project-boards) offer project management features through a [Kanban board](https://en.wikipedia.org/wiki/Kanban_board) interface.

These boards can be used to track assignment and progress of specific tasks.
This is aided by linking tasks to specific issues and pull requests.


(continuous-integration)=
## Continuous integration

Continuous integration (CI) describes the practice of frequently committing changes to your code.
This subsection relates to CI tools, which primarily help to automate routine quality assurance tasks.
These include verifying that your code successfully builds or installs and that your code tests run successfully.
As the execution environment is defined in the CI workflow configuration, running of tests in this way should be reproducible.

Automation of routine tasks in this way reduces the effort required to merge changes onto the existing code base.
This encourages frequent merging of small changes.
As such, conflicts between multiple contributions should be minimal and that review of these changes is simpler.

CI is often linked to:
* Continuous delivery - ensuring that your code is fit for use after each integration
* Continuous deployment - automatically deploying working code into production

GitHub provides a CI service via [GitHub Actions](https://github.com/features/actions).
However, many other CI tools can be integrated with version control platforms, including GitHub.
Other commonly used tools/services include:
* Jenkins
* Travis
* CircleCI
* AppVeyor


### Testing example

Below is an example configuration file, for use with GitHub actions.
The `YAML` file, which is used here, is common for CI tools.
Other CI tools may use different file types, but these likely have a similar overall structure.

```
name: Test python package

on:
  push:
    branches:
      - master
  pull_request:


jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: [3.6, 3.7, 3.8, 3.9]

    steps:
    - uses: actions/checkout@v2

    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v2
      with:
        python-version: ${{ matrix.python-version }}

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install pytest 
        pip install -r requirements.txt
        
    - name: Test with pytest
      run: |
        pytest
```

The first section of this example describes when our workflow should be run.
In this case, we're running the CI workflow whenever code is `push`ed to the `master` branch or where any Pull Request is created.
In the case of Pull Requests, the results of the CI workflow will be report on the request's page.
If any of the workflow stages fail, this can block the merge of these changes onto a more stable branch.
Subsequent commits to the source branch will trigger the CI workflow to run again.

Below `jobs`, we're defining what tasks we would like to run when our workflow is triggered.
We define what operating system we would like to run our workflow on - the Linux operating system `ubuntu` here.
The `matrix` section under `strategy` defines parameters for the workflow.
The workflow will be repeated for each combination of parameters supplied here - in this case the 4 latest Python versions.

The individual stages of the workflow are defined under `steps`.
`steps` typically have an informative name and run code to perform an action.
Here `uses: actions/checkout@v2` references [existing code](https://github.com/actions/checkout) that will retrieve the code from our repo.
The subsequent `steps` will use this code.
The next step provides us with the a working Python version, as specified in the `matrix`.
Then we install dependencies/requirements for our code and the `pytest` module.
Finally, we run `pytest` to check that our code is working as expected.

This workflow will report whether our test code ran successfully for each of the specified Python versions.


### Documentation example

This book uses the following GitHub Actions configuration to build and deploy the HTML content:

```
name: Build and deploy book

on:
  push:
    branches:
      - main
      - master
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2

    - name: Set up Python 3.7
      uses: actions/setup-python@v1
      with:
        python-version: 3.7

    - name: Install dependencies
      run: |
        pip install -r requirements.txt

    - name: Build the book
      run: |
        jb build book -W -v --keep-going && touch ./book/_build/html/.nojekyll

  deploy:
    needs: build
    runs-on: ubuntu-latest
    if: startsWith( github.ref, 'refs/tags/v')
    steps:
    - name: "Deploy book to GitHub Pages"
      uses: peaceiris/actions-gh-pages@v3.6.1
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./book/_build/html
```

This workflow runs whenever a pull request is create or changes are pushed directly to the main branch.
It has two jobs - one that builds the book's HTML content and another that deploys the content to this website.

As with the previous example, we start the workflow by setting up an environment with Python.
We install the dependencies for the project, which includes `jupyter-book` to build to the book.

Our workflow then builds the book's HTML content, where the workflow will fail if warnings or errors are raised.

In the second job, the book (including the new changes) is deployed to the site that you are reading now.
This job needs the build job to have completed successfully before it will run.
It will only run if a new Git tag has been created, to indicate a new version of the book.
This allows us to accumulate changes on the main branch, before releasing a collection of changes in the next version.
This deployment step requires authentication, which is managed by a secret/token that is accessed from the Action's environment.

You might use a similar approach to this to deploy your code's HTML documentation.


### Complex example

You can see a detailed example of CI in practice in the `jupyter-book` project.
A recent version of the [`jupyter-book` CI workflow](https://github.com/executablebooks/jupyter-book/blob/6fb0cbe4abb5bc29e9081afbe24f71d864b40475/.github/workflows/tests.yml) includes:
* Checking code against style guidelines, using [pre-commit](https://pre-commit.com/)
* Running code tests over
  * a range of Python versions
  * multiple versions of specific dependencies (`sphinx` here)
  * multiple operating systems
* Reporting test coverage
* Checking that documentation builds successfully
* Deploying a new version of the `jupyter-book` package to [the python package index (PyPI)](https://pypi.org/)


## Branching models

Adopting a particular branching model or workflow for Git can help to keep work consistent within a project.

Generally, it is good practice to:
* Commit a small number of changes, and commit often
* Use one branch per high level change (e.g. bug or feature)

These practices help to keep the audit trail informative and assist with peer review.

Here we suggest a couple of common workflows that might be used to version your analytical work.
You might not benefit from following these patterns to the the word, but should choose aspects of these to adopt a consistent workflow in your team.

These workflows are especially useful when working in a team, as they embed a peer review process into your workflow.

### Gitflow

In this workflow:
1. A development branch is created from the main branch.
2. All changes are reviewed as they are merged from individual feature branches onto this development branch.
3. Larger collections of changes are then merged from the development branch onto the main branch. These merges usually reflect a new version of functioning code.

We recommend that you use pull requests (or equivalents) to review changes that are merged onto the development and master branches.
This mode of release provides an extra opportunity for discussion and quality assurance, before changes are added to the most stable branch.

```{figure} https://nvie.com/img/git-model@2x.png
---
width: 65%
name: gitflow
alt: Branching structure when using the gitflow workflow. Features are branched from develop, which is branched from master.
---
Branching diagram to demonstrate gitflow. From [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/) by Vincent Driessen.
```

This [blog post](https://nvie.com/posts/a-successful-git-branching-model/) and the [Atlassian Gitflow guide](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) describe the workflow, with useful images to depict the branching model.


### GitHub flow

In this workflow:
1. Feature branches are created directly from the main branch.
2. Pull requests (or equivalent) are used to review and discuss changes in this new branch.
3. Once reviewed, the feature branch can be deployed for user testing.
4. Once satisfied that the code works as required, the feature branch is merged onto the main branch.

This workflow might be more suited to projects with rapid development cycles.

```{figure} https://files.programster.org/tutorials/git/flows/github-flow.png
---
width: 75%
name: github_flow
alt: Branching structure when using the GitHub flow workflow. Features branch directly from Master.
---
Branching diagram to demonstrate GitHub, from [Programster's blog post of git workflows](https://blog.programster.org/git-workflows).
```

This simple guide from GitHub also outlines [GitHub flow](https://guides.github.com/introduction/flow/#:~:text=GitHub%20flow%20is%20a%20lightweight,Created%20with%20Snap).

## Other useful resources

* [GitHub's Git Cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)
* [GitHub Git Handbook](https://guides.github.com/introduction/git-handbook/)
* [Atlassian's Learn Git](https://www.atlassian.com/git)
