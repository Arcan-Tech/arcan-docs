# arcan-docs

## How to write the docs
We use [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) to generate our documentation.

Please, refer to their docs to add new content:

- [Setup](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)
- [Reference](https://squidfunk.github.io/mkdocs-material/reference/)


## Generate a new version
```shell
mike deploy --push --update-aliases ${VERSION} latest
```