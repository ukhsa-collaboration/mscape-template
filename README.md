# mscape-template

This repository is a template for creating new repositories containing code that will run on mSCAPE. It serves as a
guide for code layout and files will need amending to fit the repo purpose.

## How to use this template:
If you are reading this README...
* **whilst in the original `mscape-template` repository**, then you can use this template to
start a new mSCAPE repo. For example, if you are on the repo page on GitHub in the browser right now, you can click the
green <span style="color:green">use this template</span> button on the top right. If you want to use this template in a
new local repo, just copy the contents of this repo into your new repo.

* **inside your own repo**, before committing to this repo, you **MUST** install the predefined
pre-commit hook. This will run ruff, some Python linting and a search for potential climb-IDs*.
    1. First [install pre-commit](https://pre-commit.com/#install):
        ```
        pip install pre-commit
        ```
    2. install the pre-commit hook into your `.git/hooks` directory using the pre-defined config in
    `.pre-commit-config.yaml`:
        ```
        pre-commit install
        ```
    3. (optional) run pre-commit against all files, to see if the current files pass the hook:
        ```
        pre-commit run --all-files
        ```
    Whenever you run `git commit` the pre-commit hook should now run automatically.

_\* Note on the climb-id search - this will match any occurence of C- followed by 5 characters of A-F or 0-9. This
__may__ match fasta sequences, such as 'AAC-CCAC...'. In this case, you may need to commit this seperately and remove
the pre-commit check for this by doing `SKIP=climb-id-checker git commit -m "add fasta sequences (skipped id check)."`_

## Repo Requirements

As a minimum, mSCAPE repositories *MUST* include the following:
- a `README.md` that explains the purpose of the repo.
- a `LICENCE` if the repo is public.
- Code to be in src/ layout
- `tests/` folder at same level as `src/`
- .github/ folder containing workflows and a pull request template
- .gitignore file
- pyproject.toml file
- .pre-commit-hooks.yaml

This repo follows the above structure and contains examples of the files
referenced above.

### Commit practices
Commits **MUST** be:

* small and focused
* clearly described

You **may** wish to use the [conventional commits format](https://www.conventionalcommits.org/en/v1.0.0/).

### Bramching Strategy
UKHSA Engineering Standards suggest we **should** follow the
[GitHub Flow-style](https://docs.github.com/en/get-started/using-github/github-flow) branching model.

    feature/ — functional changes
    bugfix/ — defect fixes
    spike/ — experimental work (not merged)
    hotfix/ — urgent fixes to production

### Branch protection
Branch protection should be inplace, preventing pushing to default branch (usually main), requiring reviewed
pull requests etc.

[Read the UKHSA Engineering Standards guidelines for more information.](https://ukhsa-collaboration.github.io/standards-org/development-standards/appendix/branch-protection-rules/)

### Pull Requests and merge process
Pull requests **MUST** be reviewed before merging and must pass all required checks.

These checks include:
- linting and formatting
- searching for climb-IDs

<br><br>

---------------------
# README template

A suggested layout for repo READMEs is included below. The guidance
documentation contains further information on required repository
structure, development cycles, and making pull requests. Please read
this guidance document before using the template.

# Project or Repo Name

Brief description of project here

## Installation

Add installation instructions here. Ideally include commands to make
the process as easy as possible for users.

Clone repo and create environment:
`git clone git@github.com:ukhsa-collaboration/project-name.git`

`conda env create -n project-name `

`conda activate project-name`

Installation for users:
`cd project-name`
`pip install .`

Installation for developers (installs code in editable mode):
`cd project-name`
`pip install --editable '.[dev]'`

## Usage

Include command line arguments (e.g. the output displayed when using -h)
for reference. Example commands can also be helpful.
```
project-name --input <path> --output <path>
```

## Inputs (optional - useful if you have a CLI)

You may wish to use a table to list out the args:

| Argument | Required | Description |
| -------- | ------- | ------- |
| --input, -i | Yes | Input for command line use  |
| --output, -o | Yes | Output for command line use  |

## Outputs (optional - useful if your tool creates lots of output files)

Explain the output files in detail here.

## Other sections

Add other sections as appropriate for your repo. This may include
instructions on updating the repo, instructions on adding new
references, troubleshooting etc.
