# ISO XXX - DocTags: Universal Document Markup Format

## Foreword

This document was prepared by Peter Staar, ... (please add yourself)

This International Standard specifies the DocTags format, a universal markup language for representing structured document content with semantic, spatial, and formatting information.

## Introduction

The proliferation of digital documents across diverse formats (PDF, HTML, Word, etc.) has created significant challenges in document processing, conversion, and understanding. Current approaches often result in loss of semantic information, structural relationships, or spatial context during document conversion.

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
| `<inline>`| Inline text grouping |
| `<ordered_list>`| Unspecified grouping |
| `<unordered_list>`| Unspecified grouping |
| `<section_level_N>` | Section header (N starts with 1) |
| `<chapter>` | Section header (N starts with 1) |

#### **location token**

These tokens represent a numerical value and follow the format `<loc_ll_rr>` where `rr` represents the dimension in integer resolution (default is 512). `ll` represents the integer location in the page (and thus `0<=ll<=r`). 

there are a few conventions:
- A coordinate (x, y) is defined as 2 location tokens with the convention of `<loc_x0><loc_y0>` and `x0<=x1` and `y0<=y1`.
- Bounding boxes are represented as 4 location tokens with the convention of `<loc_x0><loc_y0><loc_x1><loc_y1>` and `x0<=x1` and `y0<=y1`. 

#### **structural token**

The structural tokens are used to represent complex structural elements such as tables, forms, key-value regions etc.

##### **structural tokens for tables**: OTSL

| Token | Description |
|-------|-------------|
| `<otsl>` | start of table data structure |
| `<dcel/>`| Diagonal cell with content (text follows token) |
| `<fcel/>`| Cell with content (text follows token) |
| `<ecel/>`| Empty cell |
| `<lcel/>`| Left-looking cell (horizontal span) |
| `<ucel/>`| Up-looking cell (vertical span) |
| `<xcel/>`| Cross cell (2D span) |
| `<nl/>`| New line (row separator) |
| `<ched/>`| Column header (text follows token) |
| `<rhed/>`| Row header (text follows token) |
| `<srow/>`| Section row (text follows token) |

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
| `<list_marker>`| content of marker (eg `i`, `ii`, etc) for list items, section-headers, etc |
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

Note that the page breaks can be introduced in certain groupings (more on that in the section `page-breaks and continuation`)

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

























#### 6.1.2 Structural Elements

| Token | Description | Closing Required |
|-------|-------------|------------------|
| `<document_index>` | Table of contents or index | 
| `<page_break/>` | Page boundary marker | No (self-closing) |

### 6.2 List Elements

```xml
<ordered_list>
  <list_item>First item</list_item>
  <list_item>Second item</list_item>
</ordered_list>

<unordered_list>
  <list_item>Bullet item</list_item>
  <list_item>Another item</list_item>
</unordered_list>
```

### 6.3 Floating Elements

#### 6.3.1 Tables

Tables use the OTSL vocabulary within `<otsl>` tags. All OTSL cell tokens are self-closing:

```xml
<otsl>
  <loc_100/><loc_50/><loc_400/><loc_150/>
  <fcel/>Header 1<fcel/>Header 2<nl/>
  <fcel/>Data 1<fcel/>Data 2<nl/>
</otsl>
```

OTSL tokens (all self-closing):

#### 6.3.2 Pictures and Charts

```xml
<picture>
  <loc_100/><loc_50/><loc_400/><loc_350/>
  <natural_image/>
  <caption>Figure 1: Example image</caption>
</picture>

<chart>
  <loc_100/><loc_50/><loc_400/><loc_350/>
  <bar_chart/>
  <otsl><!-- chart data as table --></otsl>
  <caption>Chart 1: Sales data</caption>
</chart>
```

Picture classification tokens (self-closing):
- `<natural_image/>`, `<icon/>`, `<logo/>`, `<screenshot/>`
- `<pie_chart/>`, `<bar_chart/>`, `<line_chart/>`, `<scatter_chart/>`
- `<flow_chart/>`, `<heatmap/>`

#### 6.3.3 Formulas

```xml
<formula>
  <loc_100/><loc_200/><loc_300/><loc_250/>
  E = mc^2
</formula>
```

#### 6.3.4 Code

```xml
<code>
  <loc_50/><loc_100/><loc_450/><loc_300/>
  <_Python_/>
  def hello_world():
      print("Hello, World!")
</code>
```

Code language tokens (self-closing) follow the pattern `<_Language_/>` where Language is one of:
Ada, Awk, Bash, C, C++, C#, Python, Java, JavaScript, etc.

### 6.4 Form Elements

```xml
<key_value_region>
  <loc_50/><loc_100/><loc_450/><loc_200/>
  <key_1><loc_50/><loc_100/><loc_200/><loc_130/>Name:<link_2/></key_1>
  <value_2><loc_210/><loc_100/><loc_450/><loc_130/>John Doe</value_2>
</key_value_region>
```

### 6.5 Spatial Location

#### 6.5.1 Basic Location Tokens

Location tokens are self-closing and encode normalized coordinates:

```xml
<loc_0/>    <!-- coordinate at position 0 -->
<loc_256/>  <!-- coordinate at position 256 (center at default resolution) -->
<loc_511/>  <!-- coordinate at position 511 (maximum at default resolution) -->
```

#### 6.5.2 Location Resolution

The default resolution is 512x512. Custom resolutions MAY be specified:

```xml
<loc_34_1024/>   <!-- coordinate 34 on a 1024-resolution grid -->
<loc_128_256/>   <!-- coordinate 128 on a 256-resolution grid -->
<loc_1000_2048/> <!-- coordinate 1000 on a 2048-resolution grid -->
```

Resolution format: `<loc_VALUE_RESOLUTION/>` where:
- VALUE is the coordinate position (0 to RESOLUTION-1)
- RESOLUTION is the grid size (powers of 2 recommended: 256, 512, 1024, 2048)

#### 6.5.3 Bounding Box Specification

A bounding box is specified by four consecutive location tokens:

```xml
<loc_x1/><loc_y1/><loc_x2/><loc_y2/>
```

Mixed resolutions within the same bounding box are NOT RECOMMENDED:

```xml
<!-- NOT RECOMMENDED -->
<loc_100/><loc_50_1024/><loc_400/><loc_150_1024/>

<!-- RECOMMENDED - consistent resolution -->
<loc_100_1024/><loc_50_1024/><loc_400_1024/><loc_150_1024/>
```

## 7 Formatting and Text Direction

### 7.1 Inline Formatting

Inline formatting MAY be preserved through nested tags or escape sequences:
- Bold, italic, underline, strikethrough
- Superscript, subscript
- Text direction markers

### 7.2 Text Direction

Text direction SHALL be indicated using:
- Default: left-to-right (LTR)
- Right-to-left (RTL) content marked explicitly
- Bidirectional text handled according to Unicode standards

## 8 Complex Structures

### 8.1 Nesting Rules

Elements SHALL nest according to these rules:
1. Block elements cannot be nested within inline elements
2. List items MUST be direct children of list containers
3. Captions MUST immediately follow their associated element
4. Footnotes MAY appear anywhere within text content
5. Self-closing tokens MUST NOT have content between opening and closing tags

### 8.2 Cross-References

Internal references use self-closing link syntax:

```xml
<text>See Table <link_table_1/>1 for details.</text>
<otsl id="table_1">
  <!-- table content -->
</otsl>
```

### 8.3 Multi-Column and Multi-Page Content

Content spanning multiple columns or pages SHALL maintain continuity markers:

```xml
<text continued="true">First part of text...</text>
<column_break/>
<text continuation="true">...continuation of text</text>
```

## 9 Metadata and Annotations

### 9.1 Document Metadata

Metadata MAY be included in the document header:

```xml
<doctag_v1>
  <metadata>
    <title>Document Title</title>
    <author>Author Name</author>
    <date>2024-01-01</date>
    <language>en</language>
    <default_resolution>1024</default_resolution>
  </metadata>
  <!-- document content -->
</doctag_v1>
```

### 9.2 Element Annotations

Elements MAY include annotations for additional semantic information:

```xml
<text confidence="0.95" source="ocr">Extracted text</text>
```

## 10 Validation

### 10.1 XML Compliance

All DocTags documents MUST be well-formed XML:
1. Self-closing tags MUST use the `/>` syntax
2. All non-self-closing tags MUST have corresponding closing tags
3. Tags MUST be properly nested
4. Attribute values MUST be quoted

### 10.2 Syntax Rules

1. Location tokens MUST be self-closing
2. Location values MUST be within range [0, RESOLUTION-1]
3. OTSL cell tokens MUST be self-closing
4. Table structures MUST form valid rectangular grids

### 10.3 Semantic Rules

1. Section headers MUST use appropriate level numbers (1-6)
2. List items MUST be within list containers
3. Table cells MUST align to form complete rows and columns
4. Captions MUST be associated with floating elements
5. Version numbers MUST be positive integers

## 11 Implementation Requirements

### 11.1 Parser Requirements

A conforming parser SHALL:
1. Recognize all tokens defined in this standard
2. Support both default (512) and custom location resolutions
3. Handle self-closing tags correctly
4. Process versioned document roots
5. Preserve element ordering and hierarchy

### 11.2 Serializer Requirements

A conforming serializer SHALL:
1. Generate valid XML-compliant DocTags syntax
2. Use self-closing tags where specified
3. Normalize location coordinates to the specified resolution
4. Include version information when appropriate
5. Ensure proper element nesting

### 11.3 Resolution Handling

Implementations SHALL:
1. Default to 512x512 resolution when not specified
2. Support resolutions from 128 to 4096
3. Maintain resolution consistency within bounding boxes
4. Convert between resolutions when necessary
5. Preserve resolution information during round-trip conversion

### 11.4 Error Handling

Processors SHALL:
1. Report XML syntax errors with line and column information
2. Validate self-closing tag usage
3. Check location value ranges against specified resolution
4. Verify version compatibility
5. Provide clear error messages

## 12 Security Considerations

Implementations SHALL:
1. Validate XML input to prevent injection attacks
2. Limit nesting depth to prevent stack overflow
3. Restrict file size to prevent resource exhaustion
4. Validate resolution values to prevent overflow
5. Sanitize external references

## 13 Backwards Compatibility

### 13.1 Version Compatibility

Processors SHALL:
1. Assume v1.0.0 when no version is specified
2. Process version 1 documents using version 1 rules
3. Report unsupported version numbers clearly
4. Maintain backward compatibility for minor versions

### 13.2 Legacy Token Support

For compatibility with pre-standard implementations:
1. Processors MAY accept non-self-closing location tokens with warnings
2. Processors MAY accept non-self-closing OTSL tokens with warnings
3. Processors SHALL generate only standard-compliant output


## Annex A (Normative) - Complete Token Reference

### A.1 Document Structure Tokens

| Token | Type | Description | Example |
|-------|------|-------------|---------|
| `<doctag>` | Container | Document root | `<doctag>...</doctag>` |
| `<doctag_vN>` | Container | Versioned document root | `<doctag_v1>...</doctag_v1>` |
| `<page_break/>` | Self-closing | Page separator | `<page_break/>` |

### A.2 Location Tokens

| Token Pattern | Type | Description | Example |
|---------------|------|-------------|---------|
| `<loc_N/>` | Self-closing | Position N at default resolution (512) | `<loc_256/>` |
| `<loc_N_R/>` | Self-closing | Position N at resolution R | `<loc_512_1024/>` |

### A.3 OTSL Tokens

| Token | Type | Description | Usage |
|-------|------|-------------|-------|
| `<fcel/>` | Self-closing | Full cell | `<fcel/>text content` |
| `<ecel/>` | Self-closing | Empty cell | `<ecel/>` |
| `<lcel/>` | Self-closing | Left-merge cell | `<lcel/>` |
| `<ucel/>` | Self-closing | Up-merge cell | `<ucel/>` |
| `<xcel/>` | Self-closing | Cross-merge cell | `<xcel/>` |
| `<nl/>` | Self-closing | New line | `<nl/>` |
| `<ched/>` | Self-closing | Column header | `<ched/>header text` |
| `<rhed/>` | Self-closing | Row header | `<rhed/>header text` |
| `<srow/>` | Self-closing | Section row | `<srow/>section text` |

## Annex B (Informative) - Examples

### B.1 Simple Document with Version

```xml
<doctag_v1>
  <title>Sample Document</title>
  <section_header_level_1>Introduction</section_header_level_1>
  <text>This is a paragraph of text.</text>
  <unordered_list>
    <list_item>First point</list_item>
    <list_item>Second point</list_item>
  </unordered_list>
</doctag_v1>
```

### B.2 Table with Location Information

```xml
<doctag>
  <otsl>
    <loc_50/><loc_100/><loc_450/><loc_200/>
    <ched/>Column 1<ched/>Column 2<ched/>Column 3<nl/>
    <fcel/>A1<fcel/>B1<fcel/>C1<nl/>
    <fcel/>A2<lcel/><lcel/><nl/>  <!-- B2-C2 merged -->
    <fcel/>A3<fcel/>B3<ucel/><nl/>  <!-- C3-C4 merged -->
    <fcel/>A4<fcel/>B4<xcel/><nl/>
  </otsl>
  <caption>Table 1: Example with merged cells</caption>
</doctag>
```

### B.3 High-Resolution Location Example

```xml
<doctag_v1>
  <metadata>
    <default_resolution>2048</default_resolution>
  </metadata>
  <picture>
    <loc_400_2048/><loc_200_2048/><loc_1600_2048/><loc_1400_2048/>
    <natural_image/>
    <caption>High-resolution positioned image</caption>
  </picture>
</doctag_v1>
```

### B.4 Mixed Content with Self-Closing Tags

```xml
<doctag>
  <text>
    <loc_100/><loc_50/><loc_400/><loc_100/>
    This document contains a formula: 
  </text>
  <formula>
    <loc_100/><loc_110/><loc_400/><loc_150/>
    E = mc^2
  </formula>
  <page_break/>
  <code>
    <loc_50/><loc_50/><loc_450/><loc_200/>
    <_Python_/>
    def calculate_energy(mass, speed_of_light=299792458):
        return mass * speed_of_light ** 2
  </code>
</doctag>
```

## Annex C (Informative) - Migration Guide

### C.1 Converting from Legacy Format

Legacy format:
```xml
<loc_100><loc_200><loc_300><loc_400>
<fcel>Content</fcel>
```

Standard format:
```xml
<loc_100/><loc_200/><loc_300/><loc_400/>
<fcel/>Content
```

### C.2 Resolution Conversion

Converting from 512 to 1024 resolution:
- Multiply coordinate values by 2
- Add resolution specifier

Example:
```xml
<!-- 512 resolution (default) -->
<loc_256/><loc_128/>

<!-- Converted to 1024 resolution -->
<loc_512_1024/><loc_256_1024/>
```

## Bibliography

1. SmolDocling: An ultra-compact vision-language model for end-to-end multi-modal document conversion
2. Optimized Table Tokenization for Table Structure Recognition
3. DoclingDocument API Specification
4. W3C XML 1.0 Specification (Fifth Edition)
5. W3C HTML5 Specification
6. ISO 32000-2:2020 (PDF 2.0)

---

**Document History**
- Version 1.0.0: Initial release
- Version 1.1.0: Added XML compliance requirements, self-closing tags, resolution specification, and versioning
- Based on DocTags implementation v1.5.0
- Incorporates OTSL specification for table structures