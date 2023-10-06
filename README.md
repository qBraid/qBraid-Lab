<img width="full" alt="qbraid_lab" src="https://github.com/qBraid/qBraid-Lab/assets/46977852/aaad15e1-9b65-4046-bda5-cc98c34ea922">

[![Documentation Status](https://readthedocs.com/projects/qbraid-qbraid-lab/badge/?version=latest&token=68a6d1a5bc7dd2aa7d0c303cad1566bb9c6e9ef559ed967b47ed7f8ede241296)](https://docs.qbraid.com/projects/lab/en/latest/?badge=latest)
[![Discord](https://img.shields.io/discord/771898982564626445.svg?color=pink)](https://discord.gg/TPBU2sa8Et)

Web-based JupyterLab deployment providing curated software tools for for researchers and developers in quantum computing.

## Build docs locally

Install requirements

```shell
pip install -r docs/requirements.txt
```

Build docs

```shell
sphinx-build -W -b html docs docs/build/html
```

View html

```
open docs/build/html/index.html
```

## Launch on qBraid

The "Launch on qBraid" button (below) can be added to any public GitHub
repository. Clicking on it automaically opens qBraid Lab, and performs a
`git clone` of the project repo into your account's home directory. Copy the
code below, and replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your GitHub
info.

[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/qBraid/qBraid.git)

Use the badge in your project's `README.md`:

```
[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git)
```

Use the badge in your project's `README.rst`:

```
.. image:: https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png
    :target: https://account.qbraid.com?gitHubUrl=https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
    :width: 150px
```
