## Jupyter/Zeppelin conversion

This repo has code for converting Zeppelin notebooks to Jupyter's ipynb format.

To install the Python pre-requisites, run:

```
pip3 install -r requirements.txt
```

To convert a notebook, run:

```
python3 jupyter-zeppelin.py note.json
```

This will create a file named using the Zeppelin note's name in the current directory. Alternatively, you can pass an output path:

```
python3 jupyter-zeppelin.py note.json Example.ipynb
```

### Supported conventions

This converter supports the following Zeppelin conventions:

* Code paragraphs are converted to code cells
* `%md` paragraphs are converted to Jupyter markdown cells
* `%html` paragraphs are converted to Jupyter code cells using cell magic `%%html`
* `%sql` paragraphs are converted to Jupyter code cells using cell magic `%%sql`
* Paragraphs with unknown magics are converted to raw cells
* TEXT output is converted to `text/plain` output
* HTML output is converted to `text/html` output; some style and JS may not work in Jupyter
* TABLE output is converted to simple `text/html` tables
  * `%html` table cells are embedded in the table HTML
  * Normal table cells are escaped and then embedded in the table HTML
