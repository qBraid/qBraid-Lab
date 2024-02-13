# Contributing

Welcome! We're delighted that you're interested in contributing to the qBraid Lab documentation. Your help is essential for keeping the project great.

## Getting started

Before you start working on a new feature or a fix, here's how you can contribute:

1. **Fork the repository**: Visit the GitHub page of our project and use the "Fork" button to create a copy of the project in your own GitHub account.
2. **Create a Development Branch**: After forking, clone the repository to your local machine and create a new branch for your development. Use a descriptive name for your branch, such as `feature-<feature-name>` or `bugfix-<bug-description>`.
3. **Commit Your Changes**: Make your changes in your development branch and commit them. Be sure to write clear, concise commit messages.
4. **Push to Your Fork**: Push your changes to your forked repository on GitHub.
5. **Create a Pull Request**: Go to the original project repository and click on "Pull Requests", then click the "New Pull Request" button

## Writing Documentation with reStructuredText

Our docs are written using reStructuredText (reST), which is the default plaintext markup language used by [Sphinx](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html). It's pretty straightforward once you get the hang of it. If you're unfamiliar, [reStructuredText Primer](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#restructuredtext-primer) is a good place to start.

## Building the Documentation Locally

To build the docs locally, start by forking and cloning the repository:

```shell
# Replace the URL with the URL of your forked version of the repository
git clone https://github.com/YOUR_USERNAME/qBraid-Lab.git
cd qBraid-Lab
```

Install sphinx and other requirements:

```shell
pip install -r docs/requirements.txt
```

Then, generate the html pages with:

```shell
sphinx-build -W -b html docs docs/build/html
```

You can also use the `make` command:

```shell
cd docs
make html
```

Both methods will run Sphinx in your shell. If the build succeeds, it will say `The HTML pages are in build/html`.
You can view the generated documentation in your local browser window (on OS X) using:

```shell
open build/html/index.html
```

You can also view it by running a web server in that directory:

```shell
cd build/html
python3 -m http.server
```

Then open your browser to `http://localhost:8000`. If you make changes to the docs that aren't reflected in subsequent builds, run

```shell
make clean html
```

which will force a full rebuild.
