# Doctags ISO-standard

This repo keeps all the documentation for the ISO standardization of doctags.

## Topics to be considered

The ISO standard for doctags has as a goal to tackle the following problems

1. Standardize the doctags format (and be 1-to-1 compatible with DoclingDocument)
2. Allow complex content to be serialized in strings, including
	1. semantic information (title, text, table, etc)
	2. content with formatting (bold, italic, etc) and text-direction
	3. location and pagination [optional] with 
	4. chart content (chart-type, table representation, )
	5. math and code (code-language)
		1. inline code/math
		2. external code snippets
		3. external equations 	
	6. complex nesting (captions, footnotes, lists)
	7. complex breaks (across columns, pages, ...) for text, tables etc
	8. internal referencing  
	9. ability to add meta-data and summaries
3. Be efficient in token representation for LLM 

### Grammar

The link to an initial grammar can be found here: [link](https://github.ibm.com/DeepSearch/SmolDocling_RL/tree/main/src/sqlreinforce/ANTLR)

### Semantic information

The [current semantic labels](https://github.com/docling-project/docling-core/blob/bbe6243833c7b360344d1293686ff279afafb555/docling_core/types/doc/labels.py#L7) are:

```
    CAPTION = "caption"
    CHART = "chart"
    FOOTNOTE = "footnote"
    FORMULA = "formula"
    LIST_ITEM = "list_item"
    PAGE_FOOTER = "page_footer"
    PAGE_HEADER = "page_header"
    PICTURE = "picture"
    SECTION_HEADER = "section_header"
    TABLE = "table"
    TEXT = "text"
    TITLE = "title"
    DOCUMENT_INDEX = "document_index"
    CODE = "code"
    CHECKBOX_SELECTED = "checkbox_selected"
    CHECKBOX_UNSELECTED = "checkbox_unselected"
    FORM = "form"
    KEY_VALUE_REGION = "key_value_region"
    GRADING_SCALE = "grading_scale"  # for elements in forms, questionaires representing a grading scale
    # e.g. [strongly disagree | ... | ... | strongly agree]
    # e.g. ★★☆☆☆
    HANDWRITTEN_TEXT = "handwritten_text"
    EMPTY_VALUE = "empty_value"  # used for empty value fields in fillable forms
```

The [current group labels](https://github.com/docling-project/docling-core/blob/bbe6243833c7b360344d1293686ff279afafb555/docling_core/types/doc/labels.py#L73) are:

```
    UNSPECIFIED = "unspecified"
    LIST = (
        "list"  # group label for list container (not the list-items) (e.g. HTML <ul/>)
    )
    ORDERED_LIST = "ordered_list"  # deprecated
    CHAPTER = "chapter"
    SECTION = "section"
    SHEET = "sheet"
    SLIDE = "slide"
    FORM_AREA = "form_area"
    KEY_VALUE_AREA = "key_value_area"
    COMMENT_SECTION = "comment_section"
    INLINE = "inline"
    PICTURE_AREA = "picture_area"
```


## Links from the LF AI&Data

