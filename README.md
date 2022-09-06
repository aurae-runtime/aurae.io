# Aurae Website

The main static website for [aurae.io](https://aurae.io).

### About

The website is built using
[material-mkdocs](https://squidfunk.github.io/mkdocs-material/) which is a
Markdown flavor and a fork of `mkdocs`. `material-mkdocs` provides features like
embedding scriptable diagrams using [mermaid](https://mermaid-js.github.io/mermaid/#/).

### Creating a New Page

Create a new page in the `/docs` folder and add the filename to the `nav` list
in [mkdocs.yml](https://github.com/aurae-runtime/aurae.io/blob/main/mkdocs.yml).
The page will then be added to the main menu of the page.

The website is updated upon a merge to main and you can follow the deployment
process under the [Actions](https://github.com/aurae-runtime/aurae.io/actions)
and check for potential build errors.

### Local development

`run.sh` allows you to work on the documentation locally. `run.sh` will launch a
docker container that will build the documentation and host it on a local web
server. The development server runs on port 8000 and will automatically pick up
on changes to the documentation, however it will **not** refresh the browser
page automatically.

### DNS

| Record             | Value                                                                           |
|--------------------|---------------------------------------------------------------------------------|
| A Record           | 185.199.108.153 185.199.109.153 185.199.110.153 185.199.111.153                 |
| AAAA Record        | 2606:50c0:8000::153 2606:50c0:8001::153 2606:50c0:8002::153 2606:50c0:8003::153 |
| CNAME www.aurae.io | aurae-runtime.github.io                                                         |


