# ZoiteChat documentation

## Getting started

* Install [Python 3](https://www.python.org/)
* Install pip for Python 3
* Install Sphinx: `python -m pip install sphinx`
* On Windows: ensure your Python 3 installation is on `PATH`
* Run `make html` to build the HTML files
* Run the Python webserver to test your changes: `make server`
  (http://localhost:8000/)


## Conventions

* 4 Spaces are used for indentation.
* Ordered or unordered lists use visual indentation, where any non-list
  subelement would use an indentation of a multiple of 4 again.

Example:

```rest
- a list item
- a list item
  with a visually indented continuation
- a list item with a sub-list
  
  - that is also visually indented
- a list item with a code block

    .. code-block:: none

        that is not visually indented
```

## Read the Docs theme skin

The HTML output keeps the existing `basicstrap` Sphinx theme, then applies the
ZoiteChat main-site skin from `_static/css/zoitechat-docs.css`.

Brand navigation links are set in `conf.py` through `html_context`, and the
header logo uses `_static/zoitechat-logo.svg`.

## ZoiteChat main-site documentation skin

The Sphinx theme includes an aggressive `zoitechat-docs.css` override and layout header/footer changes so Read the Docs follows the main ZoiteChat website visual system as closely as possible while keeping Sphinx search, tables of contents, source links, and generated documentation pages intact.

The override intentionally imports the main-site CSS tokens and component rules first, then maps Sphinx/basicstrap output onto the same header, nav, card, button, table, code, footer, and responsive patterns.
