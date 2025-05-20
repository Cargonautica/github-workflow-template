# Contributing

Welcome to the contributor guide of [GitHub Workflow Template].

## Contents

- [Contributing](#contributing)
  - [Contents](#contents)
  - [Intro](#intro)
  - [Issue reports](#issue-reports)
  - [Documentation improvements](#documentation-improvements)
  - [Code contributions](#code-contributions)
    - [Submit an issue](#submit-an-issue)
    - [Clone the repository](#clone-the-repository)
    - [Implement your changes](#implement-your-changes)
    - [Submit your contribution](#submit-your-contribution)
  - [Style guides](#style-guides)
    - [Conventional commits](#conventional-commits)
    - [Code style](#code-style)
  - [Linters](#linters)
    - [Setup local linters (optional)](#setup-local-linters-optional)
    - [Run linters on a local computer (optional)](#run-linters-on-a-local-computer-optional)
    - [Auto-format code on a local computer](#auto-format-code-on-a-local-computer)
    - [Execute only specific linter](#execute-only-specific-linter)
    - [Execute only group of linters for Yaml files](#execute-only-group-of-linters-for-yaml-files)

---

## Intro

This document focuses on getting any potential contributor familiarized with
the development processes.

Please notice, all users and contributors are expected to be **open, considerate,
reasonable, and respectful**. When in doubt, [Python Software Foundation's Code of Conduct]
is a good reference in terms of behavior guidelines.


## Issue reports

If you experience bugs or general issues with [GitHub Workflow Template], please have a look on the
[issue tracker]. If you don't see anything useful there, please feel free to fire an issue report.

> 🔵 &nbsp; Please don't forget to include the closed issues in your search. Sometimes
> a solution was already reported, and the problem is considered **solved**.

New issue reports should include information about your programming environment (e.g., operating
system, SDK version etc.) and steps to reproduce the problem. Please try also to simplify the
reproduction steps to a very minimal example that still illustrates the problem you are facing.
By removing other factors, you help us to identify the root cause of the issue.


## Documentation improvements

You can help improve the documentation of [GitHub Workflow Template] by making them more readable and
coherent, or by adding missing information and correcting mistakes.

This documentation is kept in the same repository as the project code, this means that any
documentation update is done in the same way was a code contribution.

> 🔵 &nbsp; Please notice that the GitHub web interface provides a quick way for
> proposing changes. While this mechanism can be tricky for normal code contributions,
> it works perfectly fine for contributing to the docs, and can be quite handy.

## Code contributions

### Submit an issue

Before you work on any non-trivial code contribution it's best to first create a report in the
[issue tracker] to start a discussion on the subject. This often provides additional
considerations and avoids unnecessary work.

### Clone the repository

1. Clone this copy to your local disk:

    ```bash
    git clone https://github.com/turboBasic/github-workflow-template
    cd github-workflow-template
    ```

### Implement your changes

1. Create a branch to hold your changes:

    ```console
    git switch --create feature/my-feature
    ```
    and start making changes. Never work on the main branch!

1. Start your work on this branch. Follow [style guides](#style-guides) as appropriate.

1. (_optional_) If you would like to execute linters and/or static code analysers locally, please
read the [Linters](#linters) section.

1. When you’re done editing, do:

    ```console
    git add <MODIFIED FILES>
    git commit
    ```

    to record your changes in Git. Use [Conventional commits](#conventional-commits) for your
    commit messages.

    > 🔵 &nbsp; Writing a [descriptive commit message] is highly recommended. In case of doubt, you
    > can check the commit history with:
    >
    > ```console
    > git log --graph --decorate --pretty=oneline --abbrev-commit --all
    > ```
    >
    > to look for recurring communication patterns.

1. (_optional_) If you have installed [pre-commit], please make sure to see the validation
messages from it and fix any eventual issues. Pre-commit automatically launches [MegaLinter] to
check/fix the code style in a way that is compatible with the project.

1. (_optional_) If you would like to execute linters and/or static code analysers locally, please
read the [Linters](#linters) section.

1. Don't forget to add unit tests and documentation in case your contribution adds a feature and
is not just a bugfix. Check that your changes don't break any unit tests with
`#TODO add unit test command` or `#TODO add unit test command without code coverage` to run the
unitest with or without coverage reports, respectively.

1. (_optional_) Project uses [CODEOWNERS] so in case you are introducing part of code which
requires custom ownership, add or modify [CODEOWNERS](./CODEOWNERS) files.

### Submit your contribution

1. If everything works fine, push your local branch to the remote server with:

    ```bash
    git push --set-upstream origin feature/my-feature
    ```

2. Go to the web page of your fork and click "Create pull request" to send your changes for review.

    Find more detailed information in [creating a PR]. You might also want to open PR as a draft
    first and mark it as ready for review after the feedbacks from CI system or any required fixes.

## Style guides

### Conventional commits

Project uses [Conventional commits] standart of commit messages.

### Code style

Use the following Google's style guides in your code:

- [C++ style guide]
- [Java style guide]
- [JSON style guide]
- [Kotlin style guide]
- [Markdown style guide]
- [Python style guide]
- [Shell style guide]
- [XML style guide]

## Linters

Project uses [MegaLinter] for enforcing linting and formatting rules for all programming languages
and file formats used in the project.

The list of linters and formatters used by CI can be seen in [.mega-linter.yml].

### Setup local linters (optional)

Every PR is validated by CI after pushing. Still, sometimes it is more productive to execute
trivial validation, like formatting and linting, locally. In order to do so you will need to
do a few things.

1. make sure [Docker] and [Node.js] is installed on your computer to run locally.

1. make sure [pre-commit] is installed globally, e.g. using [pipx]:

    ```bash
    pipx install pre-commit
    pre-commit install
    ```

### Run linters on a local computer (optional)

In order to validate your changes locally without pushing you can invoke linters using the
following command:

```bash
docker run --rm \
    -v /var/run/docker.sock:/var/run/docker.sock:rw \
    -v $(pwd):/tmp/lint:rw oxsecurity/megalinter:v8
```

or you can use helper using Node's [npx] runner together with a [mega-linter-runner], helper
wrapper for MegaLinter:

```bash
npx mega-linter-runner
```

> 🔵 &nbsp; Despite mega-linter-runner requires installation of Node.js, we recommend to use it, as
> it provides shorter and more concise syntax for executing MegaLinter. We will use
> mega-linter-runner in documentation examples, but every command can also be executed by providing
> the equivalent arguments to the `docker run ...` command mentioned above.

### Auto-format code on a local computer

```bash
npx mega-linter-runner --fix
```

### Execute only specific linter

```bash
npx mega-linter-runner -e ENABLE_LINTERS=XML_XMLLINT
```

### Execute only group of linters for Yaml files

```bash
npx mega-linter-runner -e ENABLE_LINTERS= -e ENABLE=YAML
```


<!-- Documentation links -->

[CODEOWNERS]: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners/
[Conventional commits]: https://www.conventionalcommits.org/
[creating a PR]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
[docker]: https://docs.docker.com/get-started/get-docker/
[GitHub Workflow Template]: https://github.com/turboBasic/github-workflow-template/
[issue tracker]: https://github.com/turboBasic/github-workflow-template/issues/
[.mega-linter.yml]: .mega-linter.yml
[MegaLinter]: https://megalinter.io/latest/
[mega-linter-runner]: https://www.npmjs.com/package/mega-linter-runner
[node.js]: https://nodejs.org/en/download/package-manager/
[pipx]: https://pipx.pypa.io/stable/
[pre-commit]: https://pre-commit.com/
[python software foundation's code of conduct]: https://www.python.org/psf/conduct/

<!-- Style guides -->

[C++ style guide]: https://google.github.io/styleguide/cppguide.html
[Java style guide]: https://google.github.io/styleguide/javaguide.html
[JSON style Guide]: https://google.github.io/styleguide/jsoncstyleguide.xml
[Kotlin style Guide]: https://developer.android.com/kotlin/style-guide
[Markdown style guide]: https://google.github.io/styleguide/docguide/style.html
[Python style guide]: https://google.github.io/styleguide/pyguide.html
[Shell style guide]: https://google.github.io/styleguide/shellguide.html
[XML style guide]: https://google.github.io/styleguide/xmlstyle.html
