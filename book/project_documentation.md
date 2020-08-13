# Project Documentation

Whether you're developing a package or collaborating on a piece of analysis, documenting your project makes it much easier for others to understand your goal and ways of working.

## README ★☆☆☆☆


When working on a collaborative or open coding project, it's good practice to describe an overview of your project in a README file.
This allows users or developers to grasp the overall goal of your project.
As well as a description of the project, it might include examples using your code or references to other associated projects.
This file can be any text type, including `.txt`, `.md`, and `.rst`, and can be associated with your automated documentation.

We suggest the following for a good README:
  
  - Short statement of intent
- Longer description describing the problem that your project solves and how it solves it
- Basic installation instructions or link to installation guide
- Example usage
- Screenshot if your project has a GUI
- Links to related projects



## Contributing Guidance ★☆☆☆☆

When collaborating, it is also useful to outline the standards used within your project.
This might include particular packages that should used for certain tasks and guidance on the [code style](code-style) used in the project.
If you plan to have contributors from outside your organisation it is useful to include a code of conduct too.
Please [see GitHub](https://docs.github.com/en/github/building-a-strong-community/adding-a-code-of-conduct-to-your-project) for advice on creating a code of conduct.

For an example, see the CONTRIBUTING file from our [gptables package](https://github.com/best-practice-and-impact/gptables/blob/master/CONTRIBUTING.md):
  
  ```
# Contributing

When contributing to this repository, please first discuss the change you wish
to make via issue, email, or any other method with the owners of this
repository before making a change.

## Pull/merge request process

1. Branch from the `dev` branch. If you are implementing a feature name it
`feature/name_of_feature`, if you are implementing a bugfix name it
`bug/issue_name`.
2. Update the README.md and other documentation with details of major changes
to the interface, this includes new environment variables, useful file
locations and container parameters.
3. Once you are ready for review please open a pull/merge request to the
`dev` branch.
4. You may merge the Pull/Merge Request in once you have the sign-off of two
maintainers.
5. If you are merging `dev` to `master`, you must increment the version number
in the VERSION file to the new version that this Pull/Merge Request would
represent. The versioning scheme we use is [SemVer](http://semver.org/).


## Code style

- We name variables using few nouns in lowercase, e.g. `mapping_names`
or `increment`.
- We name functions using verbs in lowercase, e.g. `map_variables_to_names` or
`change_values`.
- We use the [numpydoc](https://numpydoc.readthedocs.io/en/latest/format.html)
format for documenting features using docstrings.

## Review process

1. When we want to release the package we will request a formal review for any
non-minor changes.
2. The review process follows a similar process to ROpenSci.
3. Reviewers will be requested from associated communities.
4. Only once reviewers are satisfied, will the `dev` branch be released.
```

In this case we have outlined our standard practices for using version control on GitHub, the code style that we are using in the project and the review process that we follow.
We have used the [Markdown](https://daringfireball.net/projects/markdown/syntax) (`.md`) markup language for this document, which is formatted into HTML when viewed on our repository.

## User Desk Instructions ★☆☆☆☆

If your project is very user focussed, for example developing a statistic production pipeline, it is very important that the code users understand how to appropriately use your code.

These instructions should include:
  
  - How to set up an environment to run your code (including how to install dependencies)
- How to run your code
- What outputs (if any) your code or system produces and how these should be interpreted
- What quality assurance has been carried out and what further quality assurance of outputs is required
- How to maintain your project (including how to update data sources)

## Dependencies ★☆☆☆☆

The environment that your code runs in includes the machine, the operating system (Windows, Mac...), the programming language, and any external packages.
It is important to record this information to ensure reproducibility.

The simplest way to document which packages your code is dependent on, is to record them in a text file.
This is typically called `requirements.txt`.

Python packages record their dependencies within their `setup.py` file, via `setup(install_requires=...)`.
You can get a list of your installed python packages using `pip freeze` in the command line.

R packages and projects record their dependencies in a DESCRIPTION file.
Packages are listed under the `Imports` key.
You can get a list of your installed R packages using the `installed.packages()` function.

[Environment management] tools are very useful for keeping track of software and package versions used in a project.

## Vignettes ★★☆☆☆

Vignettes are a form of supplementary documentation, containing applied examples that demonstrate the intended use of the code in your project or package.
Docstrings may contain examples applying individual functional units, while vignettes may show multiple units being used together.
The term vignette is usually used with reference to R packages, for example this introduction to the [{dplyr} package](https://cran.r-project.org/web/packages/dplyr/vignettes/dplyr.html) for data manipulation.
However, the same long-form documentation is beneficial for projects in any programming language - for instance the [{pandas} basics](https://pandas.pydata.org/docs/user_guide/basics.html).

We've seen that docstrings can be used to describe individual functional code elements.
Vignettes provide a demonstration of the intended use for these classes and functions, in a realistic context.
This can help users to understand how different code elements interact, and how they might use your code in their own program.

Another good example is this vignette describing [how to design vignettes](http://r-pkgs.had.co.nz/vignettes.html) in Rmarkdown.
You can produce this type of documentation in any format, though Rmarkdown is particularly effectively at combining sections of code, code outputs and descriptive text.

You might also consider providing these examples in an interactive notebook, that users can run for themselves.

## Versioning ★★☆☆☆

[Semantic versioning](https://semver.org/) provides useful rules for versioning releases of your code.
Following these rules helps a user of your code to understand how changes in your code may affect their software.
Each level of version number indicates the extent of changes to the application programming interface (API) of your code, i.e. the code that a user interacts with directly.
Changes to the major version number indicate changes to the API that are not compatible with use of previous versions of the code.
While changes is the minor and patch numbers indicate changes that are either compatible or have no effect on the use of the code, respectively.


```{figure} ./_static/semantic_versioning.png
---
width: 70%
name: semantic_versioning
---
[Semantic versioning](https://semver.org/)
```


## Changelog ★★☆☆☆

A changelog records the major changes that have occurred to a project or package, between versioned releases of the code.

```
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2020-01-21
### Added
- `add_to_each_in_list()`
- online sphinx-generated documentation
- contribution guide

### Removed
- `subtract_to_each_in_list()`

### Changed
- Improved function documentation

### Fixed
- bug in `multiple_each_in_list()`, where output was not returned
```

Similarly to versioning, a changelog is useful for users to determine whether an update to your code is compatible with their work which may depend on your code.
It can also document which parts of your code will no longer be supported in future version and which bugs in your code have been addressed.
Your changelog can be in any format and should be associated with your code documentation, so that it is easy for users and other contributors to find.

[keep a changelog](https://keepachangelog.com/en/1.0.0/) provides a simple but effective template for recording changes to your code.

## Copyright and Licenses ★★☆☆☆

Copyright indicates ownership of work.
All material created by civil servants, ministers, government departments and their agencies are covered by [Crown copyright](https://www.nationalarchives.gov.uk/information-management/re-using-public-sector-information/uk-government-licensing-framework/crown-copyright/).
It is not essential to include a copyright notice on your work, but doing so can help to avoid confusion around ownership.

Licences outline the conditions under which others may use, modify and/or redistribute your work.
As such, including a licence with your code, is important for users and developers alike.

## Open source your code ★★☆☆☆

In government, we [support and promote open source](https://www.gov.uk/service-manual/service-standard/point-12-make-new-source-code-open) whenever possible.
[Open source](https://opensource.com/resources/what-open-source) software is software with source code that anyone can freely inspect, modify and enhance.
As a government analyst, you should aim to make all new source code open, unless justification can be provided for withholding part of your source code.

Benefits of open sourcing our code include:

* Transparency - it doesn't get much more open than publishing documented methods for our analyses
* Sharing value - others can benefit from our work, either through use or demonstration of good programming practices
* Sharing opportunity - others can contribute to and help to improve our approaches
* Feels good - we regularly benefit from open source software, so it's nice to give something back
* Attribution - open sourcing your code through public version control (e.g. GitHub) creates a public record of your contributions

Please see the [Government Data Service (GDS) guidance](https://www.gov.uk/government/publications/open-source-guidance/when-code-should-be-open-or-closed) for help deciding when code should be open or closed.
Additional security concerns for coding in the open are addressed in further [GDS guidance](https://www.gov.uk/government/publications/open-source-guidance/security-considerations-when-coding-in-the-open).

Choice of open source licence, depends largely on how you would like others to be able distribute modified versions of your work.
[Government Data Service guidelines](https://gds-way.cloudapps.digital/manuals/licensing.html#use-mit) suggest the MIT licence for code and the OGL (Open Government Licence) for documentation.