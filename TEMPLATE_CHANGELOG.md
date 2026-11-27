# Changelog

## mSCAPE Template - version 0.3.0
Updated Python version and improved some documentation and pull request template instructions. Also added changelog template.

### Changed
- Python version changed in the pyproject.toml, test-build.yml and dockerfile.
- installing some arbitrary packages in test-build.yml was removed as unecessary.
- Updated the instructions in the pull request template to make it more explicit on how to use.
- Changelog for the template itself (to record changes made to the template repo) moved to TEMPLATE_CHANGELOG.md.
- README has some more info on using the repo.
- Uncomments some of the files in gitignore.

### Added
- CHANGELOG.md: this is now a template for a changelog for a new repo.

---
---

mSCAPE Template - Version 0.2.0
Now has added features:
- updated the pre-commit config to implement search for climb IDs on commit.
- added branch protection json
- dynamic versioning through version set in __init__.py in package directory and set in pyproject.toml
- removed fixed versions of ruff so the version should match the GitHub actions.
