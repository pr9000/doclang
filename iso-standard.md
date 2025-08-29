# ISO XXX - DocTags: Universal Document Markup Format

## Foreword

This document was prepared by Peter Staar, ... (please add yourself)

This International Standard specifies the DocTags format, a universal markup language for representing structured document content with semantic, spatial, and formatting information.

## Introduction

The proliferation of digital documents across diverse formats (PDF, HTML, Word, etc.) has created significant challenges in document processing, conversion, and understanding. Current popular approach of format unification rely on conversion to various text-based formats with markup features such as Markdown, LaTeX, etc. This often result in loss of semantic information, structural relationships, or spatial context during such document conversion.

DocTags addresses these challenges by providing a minimalist, unambiguous markup format that:
- Preserves complete document structure and semantics
- Maintains spatial and layout information (if appropriate)
- Supports complex document elements including tables, formulas, code, nested lists, and charts
- Enables lossless round-trip conversion between formats regarding content

This standard builds upon research in document understanding and is intended to represent the content of a document as accurate as possible but ignores visual representation.

## Scope of DocTags

This International Standard specifies:
- The syntax and semantics of the DocTags markup language
- Rules for encoding document structure, content, and metadata
- Mechanisms for representing spatial layout and pagination
- Methods for preserving formatting and text direction
- Specifications for complex document elements (tables, charts, formulas, code, form)
- Requirements for conforming implementations

This standard is applicable to:
- Document conversion systems
- Document understanding and extraction tools
- Vision-language models for document processing
- Digital archival systems
- Accessibility tools for document content


## DocTags Structure

### Comparison to XML

- Doctags is a simplified and constrained XML
- Doctags has a finite number of tags
- Doctags does not have attributes
- Doctags is a character based 

The material in this section is based on the XML Specification (verbatim from Wikipedia). This is not an exhaustive list of all the constructs that appear in XML; it provides an introduction to the key constructs.

**Character**

An XML document is a string of characters. Every legal Unicode character (except Null) may appear in an (1.1) XML document (while some are discouraged).

**Processor and application**

The processor analyzes the markup and passes structured information to an application. The specification places requirements on what an XML processor must do and not do, but the application is outside its scope. The processor (as the specification calls it) is often referred to colloquially as an XML parser.

**Markup and content**

The characters making up an XML document are divided into markup and content, which may be distinguished by the application of simple syntactic rules. Generally, strings that constitute markup either begin with the character < and end with a >, or they begin with the character & and end with a ;. Strings of characters that are not markup are content. However, in a CDATA section, the delimiters <![CDATA[ and ]]> are classified as markup, while the text between them is classified as content. In addition, whitespace before and after the outermost element is classified as markup.

**Tag**

A tag is a markup construct that begins with < and ends with >. There are three types of tag:

- start-tag, such as <text>;
- end-tag, such as </text>;
- empty-element tag, such as <page_break/>.

There is a finite set of allowed tags in doctags, which will depend on the version. A few type of tags are allowed to have a (specific) pattern. 

**Element**

An element is a logical document component that either begins with a start-tag and ends with a matching end-tag or consists only of an empty-element tag. The characters between the start-tag and end-tag, if any, are the element's content, and may contain markup, including other elements, which are called child elements. An example is <greeting>Hello, world!</greeting>. Another is <line-break />.

### Document definition, meta data and versioning

Every DocTags document shall be wrapped in a root `<doctag>` element:

```xml
<doctag>
  <!-- document content -->
</doctag>
```

The root element MAY include a version specification. Version numbering shall follow Semantic Versioning (MAJOR.MINOR.PATCH). The root element pattern `<doctag_vN>` encodes the MAJOR version number. When no version is specified, the default is v1.0.0.

```xml
<doctag_v1.0.0>
  <!-- document content -->
</doctag_v1.0.0>
```

Meta data can be included with the document using the `<meta>` tags. Meta data is optional and the data content in the meta data needs to be in strict xml format. If meta data is included, we expect also a `<body>` tag, otherwise it is optional,

```xml
<doctag_v1.0.0>
  <meta>
    ...
  </meta>
  <body>
  <!-- document content -->
  </body>
</doctag_v1.0.0>
```

Documents may be divided into pages. For this, we will use the self-closing `<page_break/>` token:

```xml
<doctag>
  <!-- page 1 content -->
  <page_break/>
  <!-- page 2 content -->
</doctag>
```

Metadata may be included in the document header,

```xml
<doctag_v1.2.3>
  <metadata>
    <version>v1.2.3</version>
    <title>Document Title</title>
    <author>Author Name</author>
    <date>2024-01-01</date>
    <language>en</language>
    <default_resolution>1024</default_resolution>
  </metadata>
  <!-- document content -->
</doctag_v1.2.3>
```

### Token Vocabulary

There are generally speaking XX types of tokens, namely the **semantic**, **location**, **group**, **structural** (eg for tables), **content**, **formatting** and the **connection** tokens.

The interpretation of these tokens is as follows,

#### **semantic token**

These tokens represent the intent of the content in the document. In the context of documents with pagination, sementic items typically have associated locations (see `Hierarchical structure`). The list of allowed semantic tokens are, 

| Token | Description |
|-------|-------------|
| `<caption>` | Caption for floating elements | 
| `<footnote>` | Footnote content | 
| `<formula>` | Mathematical expression | 
| `<code>` | code expression | 
| `<title>` | Document or section title | 
| `<section_header_level_N>` | Section header (N starts with 1) | 
| `<text>` | Generic text content | 
| `<list_item>` | Generic text content | 
| `<page_header>` | Page header content | 
| `<page_footer>` | Page footer content | 
| `<checkbox_selected>` | Generic text content | 
| `<checkbox_unselected>` | Generic text content | 
| `<document_index>` | Generic text content | 
| `<table>` | Generic text content | 
| `<form>` | Generic text content | 
| `<picture>` | Generic text content | 


#### **group token**

These tokens allow the semantic content to be grouped. The list of allowed grouping tokens are, 

| Token | Description |
|-------|-------------|
| `<group>`| Unspecified grouping |
| `<section>` | Section |
| `<inline>`| Inline text grouping |
| `<ordered_list>`| Unspecified grouping |
| `<unordered_list>`| Unspecified grouping |

#### **location token**

These tokens represent a numerical value and follow the format `<loc_ll_rr>` where `rr` represents the dimension in integer resolution (default is 512). `ll` represents the integer location in the page (and thus `0<=ll<=r`). 

there are a few conventions:
- A coordinate (x, y) is defined as 2 location tokens with the convention of `<loc_x0><loc_y0>`.
- Bounding boxes are represented as 4 location tokens with the convention of `<loc_x0><loc_y0><loc_x1><loc_y1>` and `x0<=x1` and `y0<=y1`. 

#### **structural token**

The structural tokens are used to represent complex structural elements such as tables, forms, key-value regions etc.

##### **Structural tokens for tables**: OTSL

Tabular structure and header semantics in DocTags represented by optimized table-structure language (OTSL) tokens.
Each new cell OTSL token (`<fcel/>` with it's semantic variants) is interleaved by the sequence of approptiate table cell content tokens (texts, lists, etc.).
OTSL representation has minimized vocabulary and specific rules.
The benefits of describing tables with OTSL in reducing number of structural tokens (5 essential in OTSL vs 28+ in HTML) and shorten structural sequence length to half of HTML representation on average.
Structural tokens define the structure of a table: columns, rows, cells, merged cells. Each cell can then be specified with semantic vatiant token if it's: column-header, row-header, section row separator, or corner-header.
Semantic variants of `<fcel/>` token are following the same rules as `<fcel/>` token, and used just to distinguish a function of a table cell: type of header or separator.

| Token | Semantic variant | Description |
|-------|---------|-------------|
| `<otsl>` | - | start of table data structure |
| `<fcel/>`| `<fcel/>` | a new cell |
|          | `<ched/>`| a new column header cell |
|          | `<rhed/>`| a new row header cell |
|          | `<corn/>`| a new corner header cell |
|          | `<srow/>`| a new section row cell |
| `<lcel/>`| - | left-looking cell, merging with the left neighbor cell to create a horizontal span |
| `<ucel/>`| - | up-looking cell, merging structure with the upper neighbor cell to create a vertical span |
| `<xcel/>`| - | cross cell to merge with both left and upper neighbor cells, for 2D spans |
| `<nl/>`| - | new line, table row separator |

OTSL enables easy error detection and correction during sequence generation, making it LLM friendly.
A notable attribute of OTSL is that it has the capability of achieving lossless conversion to HTML.

The OTSL representation follows these syntax rules:

- Left-looking cell rule: The left neighbour of an `<lcel/>` must be either another `<lcel/>` or one of the variants of `<fcel/>`.
- Up-looking cell rule: The upper neighbour of a `<ucel/>` must be either another `<ucel/>` or one of the variants of `<fcel/>`.
- Cross cell rule: The left neighbour of an `<xcel/>` cell must be either another `<xcel/>` or a `<ucel/>`, and the upper neighbour of an `<xcel/>` must be either another `<xcel/>` or an `<lcel/>`.
- First row rule: Only `<lcel/>` and `<fcel/>`(with variants) are allowed in the first row.
- First column rule: Only `<ucel/>` cells and `<fcel/>`(with variants) are allowed in the first column.
- Rectangular rule: The table representation of structural OTSL tokens is always rectangular - all rows must have an equal number of OTSL tokens, terminated with `<nl/>` token.


##### **structural tokens for forms**: 

| Token | Description |
|-------|-------------|
| `<key>`| Cell with content (text follows token) |
| `<implicit_key>`| Cell with content (text follows token) |
| `<value>`| Empty cell |

#### **content token**

The content tokens specify what is contained in the items and how the content can flow across page breaks. Whatever is contained within the `<content> ... </content>` tokens can be taken "as is". This allows for the mentioning of key-items without breaking the XML structure.

| Token | Description |
|-------|-------------|
| `<content>`| content of the item |
| `<marker>`| content of marker (eg `i`, `ii`, etc) for list items, section-headers, etc |
| `<class>`| associate a class (eg language, chart type, coding-language, etc) |
| `<continue_N>`| Indicate that the content continues in another document item (N starts with 1) |

#### **formatting token**

| Token | Description |
|-------|-------------|
| `<bold>`| ... |
| `<italic>`| ... |
| `<strike_through>`| ... |
| `<sup>`| ... |
| `<sub>`| ... |
| `<right_to_left>` | ... |

#### **protected metadata tokens**

| Token | Description |
|-------|-------------|
| `<author>`| ... |
| `<version>`| ... |

#### **Class tokens**

Not yet sure about this: Picture classification tokens (self-closing):

- `<natural_image/>`, `<icon/>`, `<logo/>`, `<screenshot/>`
- `<pie_chart/>`, `<bar_chart/>`, `<line_chart/>`, `<scatter_chart/>`
- `<flow_chart/>`, `<heatmap/>`


### Grammar

DocTags supports hierarchical nesting of elements to represent document structure:

- Block-level elements (paragraphs, sections, tables)
- Inline elements (formatting)
- Container elements (lists, groups)

#### Hierarchical structure

Doctags natively supports hierarchical structure. This grouping is done either via grouping elements or through semantic elements. Semantic elements that are of type `text` (see table in **semantic token** section) can only have `<inline>` group as a child. Semantic elements that are of type `structure` can have caption, footnotes and other structural data fields (eg `otsl`). A very simple example of a document is,

```xml
<doctag>
  <title><!-- title content --></title>
  <section_header_1>Abstract</section_header_1> 
  <text>Lorem ipsum ... </text>
  <section_header_1>Introduction</section_header_1> 
  ...
</doctag>
```

Note that the above has no explicit grouping. If you want it explicit, one can introduce groupings,

```xml
<doctag>
  <title><!-- title content --></title>
  <section_level_1>
    <section_header_1>Abstract</section_header_1> 
    <text>Lorem ipsum ... </text>
  </section_level_1>
  <section_level_1>
    <section_header_1>Introduction</section_header_1> 
    ...
    <page_break/>
    ...
    <!-- page 2 content -->
  </section_level_1>
</doctag>
```

Note that the page breaks can be introduced in certain groupings (more on that in the section `page-breaks and continuation`).

There are a few strict patterns with semantic and grouping elements. These are for lists, tables, forms, code and pictures,

##### **lists**

We have two types of lists, namely the ordered and unordered list. Each child of a list-group can only be of type `<list_item>`, ` <checkbox_selected>` or `<checkbox_unselected>`. The opposite is also true, the parent of `<list_item>`, ` <checkbox_selected>` or `<checkbox_unselected>` can only be a `<ordered_list>` or `<unordered_list>`. List items can specify their custom markers using the `<marker>` token.

```xml
<ordered_list>
  <list_item>First item</list_item>
  ...
  <unordered_list>
    <list_item><marker>*</marker>Bullet item</list_item>
    ...
  </unordered_list>
  <unordered_list>
    <checkbox_selected>Bullet item</checkbox_selected>
    ...
  </unordered_list>
</ordered_list>
```

##### **tables**

Tables have at most three direct children, namely `<caption>`, `<otsl>` and `<footnote>`. Each of them can of course of location tokens, unless we have list-groups 

```xml
<table>
  <caption><loc_100/><loc_20/><loc_400/><loc_30/>
  Table 1. Lorem Ipsum ...
  </caption>
  <otsl><loc_100/><loc_50/><loc_400/><loc_150/>
    <fcel/>Header 1<fcel/>Header 2<nl/>
    <fcel/>Data 1<fcel/>Data 2<nl/>
  </otsl>
  <footnote>
    <unordered_list>
      <list_item><loc_100/><loc_160/><loc_400/><loc_180/><marker>*</marker>Lorem Ipsum ...</list_item>
      ...
    </unordered_list>
  </footnote>
</table>
```

We use the OTSL vocabulary within `<otsl>` tags to capture the structure of the table. All OTSL cell tokens are self-closing and follow a strict pattern with the following rules,

1. every atomic row (== row-span 1) has the exact same number of of otsl tokens and ends with `<nl/>`
2. every <lcell/>, <ucell/> or <xcell/> is needs to point to an <fcell/>, <ecell/>, <rhed/> or <ched/>. 
3. the content of every otsl cell can be of arbirary hierachical structure

##### **pictures**

Pictures are similar to table.

```xml
<picture>
  <caption><loc_100/><loc_20/><loc_400/><loc_30/>
  Picture 1. Lorem Ipsum ...
  </caption>
  <picture><loc_100/><loc_50/><loc_400/><loc_150/></picture>
  <footnote>
    <unordered_list>
      <list_item><loc_100/><loc_160/><loc_400/><loc_180/><marker>*</marker>Lorem Ipsum ...</list_item>
      ...
    </unordered_list>
  </footnote>
</picture>
```

You can have grouped pictures,

```xml
<picture>
  <caption><loc_100/><loc_20/><loc_400/><loc_30/>
  Picture 1. Lorem Ipsum ...
  </caption>
  <group>
    <picture><loc_100/><loc_50/><loc_200/><loc_150/></picture>
    <picture><loc_300/><loc_50/><loc_400/><loc_150/></picture>
    ...
  </group>
</picture>
```

You can also have OTSL data associated with pictures (eg for charts)

```xml
<table>
  <caption><loc_100/><loc_20/><loc_400/><loc_30/>
  Picture 1. Lorem Ipsum ...
  </caption>
  <picture><loc_100/><loc_50/><loc_400/><loc_150/>
    <class>bar_chart</class>
    <otsl>
      <fcel/>year<fcel/>revenue<nl/>
      <fcel/>2020<fcel/>1.543M<nl/>
    </otsl>
  </picture>
</table>
```

#### Formulas

```xml
<formula>
  <loc_100/><loc_200/><loc_300/><loc_250/>
  E = mc^2
</formula>
```

#### Code

```xml
<code>
  <loc_50/><loc_100/><loc_450/><loc_300/>
  <class>Python</class>
  def hello_world():
      print("Hello, World!")
</code>
```

### Form

```xml
<form><loc_50/><loc_100/><loc_450/><loc_200/>
  <unordered_list>
    <list_item><loc_50/><loc_100/><loc_200/><loc_130/>
      <key>Name:</key>
      <value>John</value>
    </list_item>
    <list_item><loc_50/><loc_100/><loc_200/><loc_130/>
      <blind_key></blind_key>
      <value>19 Dec 2020</value>
    </list_item>
    <checked_box>Male
    </checked_box>
    <unchecked_box>Female
    </unchecked_box>
    ...
  </unordered_list>
</form>
```

### Inline structure

The inline structure allows the document to have complex representation of text. Children of the inline group are not required to have location tokens. 

```xml
<inline><loc_50/><loc_100/><loc_200/><loc_130/>
  <text>The superconducting transition temperature</text>
  <formula>T^c</formula>
  ...
</inline>
```

For any complex notation in text items (including section-headers, list-items, text items, captions etc). Notice that inline groups can also be used to capture flowing text across columns, eg

```xml
<inline>
  <inline><loc_50/><loc_100/><loc_100/><loc_130/>
    <text>The superconducting transition temperature</text>
    <formula>T^c</formula>
    ...
  </inline>
    <inline><loc_110/><loc_100/><loc_200/><loc_130/>
    ...
  </inline>
</inline>  
```

### Formatting

Formatting may be preserved through nested tags or escape sequences:

- Bold, italic, underline, strikethrough
- Superscript, subscript
- Text direction markers

### Page breaking

Page breaks are complex components that interupt the flow of a document. They can interupt paragraphs, tables, lists, etc. In general, we follow two rules,

1. If we have content that jumps over one (or more) page-breaks, we append the `<continue_N>` token to the item. The same token is then used in the beginning of the item that continues the content.
2. For the follow up content of the page, we follow a reading order and close all open tokens before the `<page_break/>` token is introduced.

An easy example is below,

```xml
<doctags>
  <text>...<continue_1/></text>
  <page_break/>
  <text><continue_1/>...</text>
</doctags>
```

A more complicated example is below in which we break the content of a list-item,

```xml
<doctags>
  <ordered_list>
    <list_item>First item</list_item>
    <list_item>Second <continue_1/></list_item>
    ...
  </ordered_list>
  <page_footer>...</page_footer>
  <page_break/>
  <ordered_list>
    <list_item><continue_1/> Item</list_item>
  </ordered_list>
  ...
</doctags>
```

#### Table breaking

For tables that are broken across pages, we need to introduce two differnt tokens, namely the `<continue_col_N/>` and `<continue_row_N/>`.


## Implementation Requirements

### Parser Requirements

A conforming parser SHALL:
1. Recognize all tokens defined in this standard
2. Support both default (512) and custom location resolutions
3. Handle self-closing tags correctly
4. Process versioned document roots
5. Preserve element ordering and hierarchy

### Serializer Requirements

A conforming serializer SHALL:
1. Generate valid XML-compliant DocTags syntax
2. Use self-closing tags where specified
3. Normalize location coordinates to the specified resolution
4. Include version information when appropriate
5. Ensure proper element nesting

### Resolution Handling

Implementations SHALL:
1. Default to 512x512 resolution when not specified
3. Maintain resolution consistency within bounding boxes
4. Convert between resolutions when necessary
5. Preserve resolution information during round-trip conversion

## Bibliography

1. SmolDocling: An ultra-compact vision-language model for end-to-end multi-modal document conversion
2. Optimized Table Tokenization for Table Structure Recognition
3. DoclingDocument API Specification
4. W3C XML 1.0 Specification (Fifth Edition)
5. W3C HTML5 Specification
6. ISO 32000-2:2020 (PDF 2.0)

## Appendix A: Advanced examples