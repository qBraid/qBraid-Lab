<img width="full" alt="qbraid_lab" src="https://github.com/qBraid/qBraid-Lab/assets/46977852/aaad15e1-9b65-4046-bda5-cc98c34ea922">

Web-based JupyterLab deployment providing curated software tools for for researchers and developers in quantum computing.


### Build docs locally

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
