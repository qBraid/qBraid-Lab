<img width="full" alt="qbraid_lab" src="https://github.com/qBraid/qBraid-Lab/assets/46977852/aaad15e1-9b65-4046-bda5-cc98c34ea922">

[![Documentation Status](https://readthedocs.com/projects/qbraid-qbraid-lab/badge/?version=latest&token=68a6d1a5bc7dd2aa7d0c303cad1566bb9c6e9ef559ed967b47ed7f8ede241296)](https://docs.qbraid.com/projects/lab/en/latest/?badge=latest)
[![GitHub](https://img.shields.io/badge/issue_tracking-github-blue?logo=github)](https://github.com/qBraid/qBraid-Lab/issues)
[![Discord](https://img.shields.io/discord/771898982564626445.svg?color=pink)](https://discord.gg/TPBU2sa8Et)

[qBraid Lab](https://lab.qbraid.com) is a web-based JupyterLab deployment providing curated software tools for
for researchers and developers in quantum computing.

[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/qBraid/qBraid.git)

## Features

- Hosts **30+** configurable quantum software environments in **Python**, **Julia**, **C++**, and **Q#**.
- Integrates with **GitHub**, **VSCode**, **ChatGPT**, and more.
- **Collaborative tools** enable sharing notebooks, environments, and code snippets.
- Provides direct access to a robust suite of computing resources, encompassing scalable **CPUs**, **GPUs**, and **QPUs**.

## Resources

- [Developer documentation](https://docs.qbraid.com/projects/lab/)
- [Example notebooks](https://github.com/qBraid/qbraid-lab-demo)
- [Project Jupyter](https://docs.jupyter.org/en/latest/#jupyter-project-documentation)
- [JupyterLab](https://jupyterlab.readthedocs.io/en/stable)
- [Jupyter Notebook](https://jupyter-notebook.readthedocs.io/en/latest/notebook.html)

## This repository

qBraid Lab and its extensions are proprietary and closed source. However, this repository hosts the Sphinx documentation source as open-source, licensed under [Apache-2.0](LICENSE), to enable community members to contribute to, revise, and enhance the documentation. Additionally, this repository serves as a platform for tracking community [feature requests](https://github.com/qBraid/qBraid-Lab/issues/new?assignees=&labels=type%3A+feature+request&projects=&template=feature_request.yml) and [bug reports](https://github.com/qBraid/qBraid-Lab/issues/new?assignees=&labels=type%3A+bug&projects=&template=bug_report.yml).

- For topics related to **qBraid-Lab**, please open an issue [here](https://github.com/qBraid/qBraid-Lab/issues).
- For topics related to **qBraid-SDK**, please open an issue [here](https://github.com/qBraid/qBraid/issues).
- For topics related to **qBraid-QIR**, please open an issue [here](https://github.com/qBraid/qbraid-qir).
- For topics related to [account](https://account.qbraid.com), [qbook](https://qbook.qbraid.com), or other qBraid services, please open an issue [here](https://github.com/qBraid/community).

## Getting started

To use qBraid Lab, you must first [sign in](https://account.qbraid.com) or [create an account &rarr;](account.qbraid.com).

Use the drop-down at the top of your [account page](https://account.qbraid.com) to select a Lab image. All users
have access to the "Free" tier image, which includes 2 virtual CPUs and 4 GB of RAM. [Paid subscription tiers](https://www.qbraid.com/products)
include compute options ranging up to 10 virtual CPUs, GPU images, and application specific
images such as [Bloqade](https://docs.qbraid.com/projects/lab/en/latest/lab/bloqade.html). Once you have selected an image, click **Launch Lab**.

Once your image is pulled, you will be taken to the qBraid Lab interface. Here are a few helpful resources to get started:

- **Interactive tour**: Click **Start Tour** (bottom right) to begin a guided tour of all of the Lab extensions and their key features.
- **qBraid tutorials**: The ``qbraid-tutorials`` directory (left-sidebar **FILES** tab) contains examples and tutorials for a wide range different quantum software packages. Many of the notebooks contain qBraid instructions and are runnable using the ``Python 3 [Default]`` environment.
- **qBraid Docs**: The **Quantum Docs** extension (bottom middle of Launcher, under **Other**) contains a collection of direct links to documentation pages for many of the most popular quantum software packages.
- **Help drop-down**: The top-bar menu **Help** drop-down contains links to more qBraid user guides, demos, and reference materials.

![launcher](docs/_static/getting_started/launcher.png)

## User Guide

- [Account](https://docs.qbraid.com/projects/lab/en/latest/lab/account.html)
  - [Add access key](https://docs.qbraid.com/projects/lab/en/latest/lab/account.html#add-access-key)

- [Getting Started](https://docs.qbraid.com/projects/lab/en/latest/lab/getting_started.html)
  - [Launch Lab](https://docs.qbraid.com/projects/lab/en/latest/lab/getting_started.html#launch-lab)
  - [Lab interface](https://docs.qbraid.com/projects/lab/en/latest/lab/getting_started.html#lab-interface)
  - [Lab server](https://docs.qbraid.com/projects/lab/en/latest/lab/getting_started.html#lab-server)

- [Environments](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html)
  - [Install environment](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#install-environment)
  - [Create environment](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#create-environment)
  - [Share environment](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#share-environment)
  - [Uninstall / cancel install environment](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#uninstall-cancel-install-environment)
  - [Install new package](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#install-new-package)
  - [Activate environment (kernel)](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#activate-environment-kernel)
  - [Command-line usage](https://docs.qbraid.com/projects/lab/en/latest/lab/environments.html#command-line-usage)

- [Kernels](https://docs.qbraid.com/projects/lab/en/latest/lab/kernels.html)
  - [Add/remove kernels](https://docs.qbraid.com/projects/lab/en/latest/lab/kernels.html#add-remove-kernels)
  - [Julia](https://docs.qbraid.com/projects/lab/en/latest/lab/kernels.html#julia)
  - [C++](https://docs.qbraid.com/projects/lab/en/latest/lab/kernels.html#c++)

- [Notebooks](https://docs.qbraid.com/projects/lab/en/latest/lab/notebooks.html)
  - [Create notebook](https://docs.qbraid.com/projects/lab/en/latest/lab/notebooks.html#create-notebook)
  - [Switch notebook kernel](https://docs.qbraid.com/projects/lab/en/latest/lab/notebooks.html#switch-notebook-kernel)
  - [Share notebook](https://docs.qbraid.com/projects/lab/en/latest/lab/notebooks.html#share-notebook)

- [Quantum Devices](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_devices.html)
  - [Quantum Devices Sidebar](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_devices.html#quantum-devices-sidebar)

- [Quantum Jobs](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_jobs.html)
  - [Credits](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_jobs.html#credits)
  - [Which environments?](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_jobs.html#which-environments)
  - [Enable/disable](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_jobs.html#enable-disable)
  - [Manage](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_jobs.html#manage)

- [Code Snippets](https://docs.qbraid.com/projects/lab/en/latest/lab/code_snippets.html)
  - [Key Features](https://docs.qbraid.com/projects/lab/en/latest/lab/code_snippets.html#key-features)

- [GPUs](https://docs.qbraid.com/projects/lab/en/latest/lab/gpu.html)
  - [Launch GPU instance](https://docs.qbraid.com/projects/lab/en/latest/lab/gpu.html#launch-gpu-instance)
  - [Configuration](https://docs.qbraid.com/projects/lab/en/latest/lab/gpu.html#configuration)
  - [GPU-enabled environments](https://docs.qbraid.com/projects/lab/en/latest/lab/gpu.html#gpu-enabled-environments)

- [Omnisearch](https://docs.qbraid.com/projects/lab/en/latest/lab/omnisearch.html)
  - [GitHub](https://docs.qbraid.com/projects/lab/en/latest/lab/omnisearch.html#omnisearch-github)
  - [ChatGPT](https://docs.qbraid.com/projects/lab/en/latest/lab/omnisearch.html#omnisearch-chatgpt)

- [Quantum Docs](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_docs.html)
  - [Browse by company](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_docs.html#browse-by-company)
  - [Company link page](https://docs.qbraid.com/projects/lab/en/latest/lab/quantum_docs.html#company-link-page)

- [Jupyter Extensions](https://docs.qbraid.com/projects/lab/en/latest/lab/extensions.html)
  - [Filebrowser](https://docs.qbraid.com/projects/lab/en/latest/lab/extensions.html#filebrowser)
  - [Git](https://docs.qbraid.com/projects/lab/en/latest/lab/extensions.html#git)
  - [Resource Usage](https://docs.qbraid.com/projects/lab/en/latest/lab/extensions.html#resource-usage)

- [Integrations](https://docs.qbraid.com/projects/lab/en/latest/lab/integrations.html)
  - [Visual Studio Code](https://docs.qbraid.com/projects/lab/en/latest/lab/integrations.html#visual-studio-code)

- [System Info](https://docs.qbraid.com/projects/lab/en/latest/lab/system.html)
  - [Operating System](https://docs.qbraid.com/projects/lab/en/latest/lab/system.html#operating-system)
  - [Pre-Installed Software](https://docs.qbraid.com/projects/lab/en/latest/lab/system.html#gnu-packages)

- [Troubleshooting](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html)
  - [Error launching Lab](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html#error-launching-lab)
  - [Lab server errors](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html#lab-server-errors)
  - [ModuleNotFoundError](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html#modulenotfounderror)
  - [NoRegionError](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html#noregionerror)
  - [Extension sidebar errors](https://docs.qbraid.com/projects/lab/en/latest/lab/troubleshoot.html#extension-sidebar-errors)

## Launch on qBraid

The "Launch on qBraid" button (below) can be added to any public GitHub
repository. Clicking on it automaically opens qBraid Lab, and performs a
`git clone` of the project repo into your account's home directory. Copy the
code below, and replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your GitHub
info.

[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/qBraid/qBraid.git)

Use the badge in your project's `README.md`:

```markdown
[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git)
```

Use the badge in your project's `README.rst`:

```rst
.. image:: https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_white.png
    :target: https://account.qbraid.com?gitHubUrl=https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
    :width: 150px
```

## Contributing

- Interested in contributing to the project, or making a PR? See
  [CONTRIBUTING.md](CONTRIBUTING.md)
- For feature requests and bug reports:
  [Submit an issue](https://github.com/qBraid/qBraid/issues)
- For discussions, and specific questions about the qBraid SDK, qBraid Lab, or
  other topics, [join our discord community](https://discord.gg/TPBU2sa8Et)
- For questions that are more suited for a forum, post to
  [Quantum Computing Stack Exchange](https://quantumcomputing.stackexchange.com/)
  with the [`qbraid`](https://quantumcomputing.stackexchange.com/questions/tagged/qbraid) tag.
- Want your open-source project featured as its own runtime environment on
  qBraid Lab? Fill out our
  [New Environment Request Form](https://forms.gle/a4v7Kdn7G7bs9jYD8)

## License

[Apache License 2.0](LICENSE)
