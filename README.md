# qBraid-Lab
Web-based JupyterLab deployment providing curated software tools for for researchers and developers in quantum computing.


### Build docs locally

Install requirements

```shell
pip install -r requirements.txt
```

Build docs

```shell
sphinx-build -W -b html . build/html
```

View html

```
open build/html/index.html
```