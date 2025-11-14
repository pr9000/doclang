# Doctags ISO standard

This repo keeps all the documentation for the ISO standardization of DocTags.

## ISO standard

The official ISO standard is described in the Markdown file [iso-standard.md](./iso-standard.md).

To create the Word document, simply run `uv run ./docling_iso/write_iso_draft.py`.

## Parser

The repo also includes a DocTags parser. You can find the grammar [here](./docling_iso/grammar.lark) and the
visualized tests [here](./test/data/test_data.md).
