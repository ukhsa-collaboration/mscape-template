# mscape-template

This repository is a template for creating new repositories containing code that will run on mSCAPE. It serves as a
guide for code layout and files will need amending to fit the repo purpose.

## How to use this template:
If you are reading this README...
* **whilst in the original `mscape-template` repository**, then you can use this template to
start a new mSCAPE repo. For example, if you are on the repo page on GitHub in the browser right now, you can click the
green <span style="color:green">use this template</span> button on the top right. If you want to use this template in a
new local repo, just copy the contents of this repo into your new repo.

* **inside your own repo**, before committing to this repo, you **MUST** do 2 things - set up branch protection on the
remote and install the predefined pre-commit hook.

1.) Set up branch protection:

    a. You should have either git cloned this repo locally, but if not, you will need the file
    `recommended-branch-protection.json` from the template repo.

    b. Go to settings in the GitHub repo in your browser. The Settings tab is under the repo name and search bar.

    c. On the banner on the right, you should see 'Rules'. Clickon the drop down, and click 'Rulesets'.

    d. Click on the green 'New Ruleset' button in the top right, and select 'Import a ruleset'.

    e. A file browser window will open, where you can select the `recommended-branch-protection.json` from your locally

    cloned repo or from the file you downloaded. Click 'open' in the file browser window to upload it.
    f. Scroll down and click the green 'Create' button.

    g. when clicking back into the 'rulesets' area from the banner on the right, you should now see
    `protect-main` with 4 rules, targetting 1 branch (which should be main).

It's a good idea to click through the rules implemented to understand what is happening.
Essentially, when applied to the `main` branch:
- Restrict deletions - can't delete `main` (only those with bypass can)
- Require a pull request before merging - Require all commits be made to a non-target branch and submitted via a pull
request before they can be merged.
- 1 required approval before pull request can be merged.
- Dismiss stale pull request approvals when new commits are pushed - New, reviewable commits pushed will dismiss
previous pull request review approvals.
- Require approval of the most recent reviewable push - most recent reviewable push must be approved by someone other
than the person who pushed it.
- Require status checks to pass - must pass tests and linting as laid out in the `.github/workflows/test-build.yml`.
- Require branches to be up to date before merging - pull requests targeting `main` must be tested with the latest code.
- Block for pushes - prevent users with push access from force pushing to `main`.

2.) The pre-commit hook. This will run ruff, some Python linting and a search for potential climb-IDs* every time you
commit locally.

    a. First [install pre-commit](https://pre-commit.com/#install):
        pip install pre-commit

    b. install the pre-commit hook into your .git/hooks directory using the pre-defined config in
    .pre-commit-config.yaml:
        pre-commit install

    c. (optional) run pre-commit against all files, to see if the current files pass the hook:
        pre-commit run --all-files

    Now, whenever you run git commit the pre-commit hook should now run automatically.

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
Branch protection should be inplace, preventing pushing to default branch (usually main), requiring reviewed pull requests etc.

[Read the UKHSA Engineering Standards guidelines for more information.](https://ukhsa-collaboration.github.io/standards-org/development-standards/appendix/branch-protection-rules/)

### Pull Requests and merge process
When you have a feature or fix ready, you can submit a merge request.
The merge request should be populated using the merge-request template. This include a checklist, and can be [found in the repo](.github/pull_request_template.md).

Essentially, read through this, choose the correct checklist for your needs - either 'writing a new component' or 'updating an existing component', delete the parts you do not need, tick the checkboxes as you make the checks, then submit for review.

You should then contact a reviewer, give the link to pull request and ideally meet to discuss what changes you have made and what you are looking for in this code review.

The reviewer should then go ahead and carry out the review as requested, and must verify the following:

- The updated code base contains no CLIMB IDs or other sensitive information. This includes test data!
- Version number bumped in pyproject.toml
- Changes have been documented in the component CHANGELOG.md
- Documentation has been updated if required
- You can install the codebase (if applicable)
- Unit tests and an end-to-end test run successfully.
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
