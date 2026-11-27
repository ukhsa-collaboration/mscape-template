# mscape-template

This repository is a template for creating new repositories containing code that
will run on mSCAPE. It serves as a guide for code layout and files will need
amending to fit the repo purpose.

There is guidance documentation including SOPs that contain further information on required repository
structure, development cycles, and making pull requests. Please read
this guidance documentation before using the template.

There is a README template below the double lines.

## How to use the template:
The template is set up for Python codebases. It is set to use Python >=3.14. It has the layout required for
installable python packages with the SRC layout. It also includes a pre-commit hook config that should be
set up before committing to the repo. It has some preset GitHub interactions, such as the recommended branch
protection json and github action workflows;
    - the 'build' action runs the install, linting and pytest when opening a PR to main.
    - The 'docker' action builds the docker container and pushes it to GHCR, and runs when a release is published.

When opening a pull request on GitHub, the provided text box will be populated with the pull-request-template in this
repo. Follow the instructions given.

The .gitignore file uses a template with many common files that should not be committed, such as build files and cache.
Common build files, caches and IDE directories are ignored already.

The TEMPLATE_CHANGELOG shows the changes to this template respository, and can be removed from your repository.
The CHANGELOG.md is a template to be used in new repositories. Remove the headers not necessary for your versions
in the CHANGELOG.md as needed.
[Read more about how to write a good changelog in the docs](https://keepachangelog.com/en/1.1.0/).

### Use a different Python version
The python version is set in the pyproject.toml, dockerbuild and test-build.yaml. To change the python
version for your code base, change it in these files.



__Below these double lines is a README template to be edited. Remove the lines and everything above them in your readme.__

---------------------
---------------------

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
