# String Replace | Find and Replace Action

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-Find%20and%20Replace-blue.svg?colorA=24292e&colorB=0366d6&style=flat&longCache=true&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAM6wAADOsB5dZE0gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAERSURBVCiRhZG/SsMxFEZPfsVJ61jbxaF0cRQRcRJ9hlYn30IHN/+9iquDCOIsblIrOjqKgy5aKoJQj4O3EEtbPwhJbr6Te28CmdSKeqzeqr0YbfVIrTBKakvtOl5dtTkK+v4HfA9PEyBFCY9AGVgCBLaBp1jPAyfAJ/AAdIEG0dNAiyP7+K1qIfMdonZic6+WJoBJvQlvuwDqcXadUuqPA1NKAlexbRTAIMvMOCjTbMwl1LtI/6KWJ5Q6rT6Ht1MA58AX8Apcqqt5r2qhrgAXQC3CZ6i1+KMd9TRu3MvA3aH/fFPnBodb6oe6HM8+lYHrGdRXW8M9bMZtPXUji69lmf5Cmamq7quNLFZXD9Rq7v0Bpc1o/tp0fisAAAAASUVORK5CYII=)](https://github.com/shitiomatic/str-replace)
[![Actions Status](https://github.com/shitiomatic/str-replace/workflows/Build/badge.svg)](https://github.com/shitiomatic/str-replace/actions)
[![Actions Status](https://github.com/shitiomatic/str-replace/workflows/Integration%20Test/badge.svg)](https://github.com/shitiomatic/str-replace/actions)

This action will find and replace strings in your project files.

## Usage

### Example workflow

This example replaces `hello` with `world` in all of your project files.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Find and Replace
      uses: shitiomatic/str-replace@master
      with:
        find: "hello"
        replace: "world"
```

### Inputs

| Input                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `find`  | A string to find and replace in your project files. _(This can be a regular expression)_   |
| `replace`  | The string to replace it with.   
| `include` _(optional)_  | A regular expression of files to include. _Defaults to `.*`._    |
| `exclude` _(optional)_  | A regular expression of files to exclude. _Defaults to `.git/`._    |

### Outputs

| Output                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `modifiedFiles`  | The number of files that have been modified    |

## Examples

### Including a subdirectory

You can limit your find and replace to a directory.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Find and Replace
      uses: shitiomatic/str-replace@master
      with:
        find: "hello"
        replace: "world"
        include: "justthisdirectory/"
```

### Filter by file name

You can limit your find and replace to just files with a specific name.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Find and Replace
      uses: shitiomatic/str-replace@master
      with:
        find: "hello"
        replace: "world"
        include: "README.md"  # Will match all README.md files in any nested directory
```

### Exclude by file type

You can set your find and replace to ignore certain file types.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Find and Replace
      uses: shitiomatic/str-replace@master
      with:
        find: "hello"
        replace: "world"
        exclude: "*.py"  # Do not modify Python files
```
