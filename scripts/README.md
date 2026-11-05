# Public APIs Scripts

This directory contains all validation and testing scripts used by Public APIs.

```bash
scripts
│   github_pull_request.sh  # used to validate changes of a pull request
│   requirements.txt  # contains dependencies of validate package
│
├───tests  # contains all unit tests from the validate package
│       test_validate_format.py
│       test_validate_links.py
│
└───validate  # validate package
        format.py
        links.py
```

## Install dependencies

You must have [python](https://www.python.org/) installed to use these scripts.

Install the validation package dependencies with [pip](https://pypi.org/project/pip/):

```bash
$ python -m pip install -r scripts/requirements.txt
```

## Run validations

From the `public-apis` repository root, run format validation on `README.md`:

```bash
$ python scripts/validate/format.py README.md
```

From the repository root, run link validation on `README.md`:

```bash
$ python scripts/validate/links.py README.md
```

The full link validation checks for duplicate URLs and makes network requests to test links, so it can take some time. To check only for duplicate URLs without making requests to the linked websites, run:

```bash
$ python scripts/validate/links.py README.md -odlc
```

*`-odlc` is an abbreviation of `--only_duplicate_links_checker`*

## Running Tests

To run all tests it is necessary to change to the scripts directory:

```bash
$ cd scripts
```

Then run:

```bash
$ python -m unittest discover tests/ --verbose
```

To run only the format tests, run:

```bash
$ python -m unittest discover tests/ --verbose --pattern "test_validate_format.py"
```

To run only the links tests, run:

```bash
$ python -m unittest discover tests/ --verbose --pattern "test_validate_links.py"
```
