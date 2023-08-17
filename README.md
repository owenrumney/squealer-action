![Squealer](.github/images/squealer.png)

# Squealer Action

Runs [Squealer](https://github.com/owenrumney/squealer) with a configurable output.

## But what is Squealer

Check the link above - but the TL;DR is that Squealer can either check the entire git history or the current folder for any secrets from a large number of patterns. 

Find out if you've accidentally committed some AWS creds to in the commit or as SLACK webhook maybe?

## Usage

### Optional Inputs

A few optional inputs are available for use;

#### Working Directory
Specify the working directory to scan, default is .

#### Format
Choose between default, json or sarif - Default is default

#### Version

Specify the version of Squealer that you want to download, otherwise it will use latest

#### github_token 
A GitHub token to be used when calling the GitHub API, which helps in avoiding rate-limiting

### Example Action

```
name: squealer
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  squealer:
    name: squealer
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master
      - name: squealer
        uses: owenrumney/squealer-action@v1.0.0
```
