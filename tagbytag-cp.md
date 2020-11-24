# Tag by tag CP

## HTML

HTML5 is the latest incarnation of a very well-known standard for coding documents. Elsevier chose HTML5 over developing a new in-house standard (like DTD56). This means that the (HTML5 recommendation)[https://www.w3.org/TR/html52/] is the main resource for finding out which elements and attributes can be used where. Luckily, this recommendation is fairly readable. There is also a wealth of information available on the internet that supplements the (understanding of) the HTML5 specification. 

This document does not aim to replicate the HTML5.2 specification - this is unnecessary given its quality. The aim is to highlight a number of features and to describe usage patterns. Unless specifically noted, the HTML5.2 specification has precedence.

### introduction

HTML elements are used to code the visible text of a document. This produces a foundational layer. Any meaning that goes above and beyond the semantics of HTML is handled at the JSON-LD level.

Traditionally, HTML is seen as a very forgiving markup vocabulary. This is mostly because browsers have been exceptional in their support of weird or even outright wrong HTML. Even though Elsevier can rely on these browsers to render HTML, using "liberal" HTML makes life more difficult for production. DTD56 XML is quite strict compared to HTML, and this is not without merit or reason. So even though the content profile standard leaves the use of HTML5 mostly open, in this document some practices are actively frowned upon.

An example of a problematic use of HTML5 is the following. If a document is converted from PDF or Word to HTML5, there might be a temptation to capture the original pages and lines with HTML tags:

```xml
<!DOCTYPE html>
<html>
    ...
    <body>
        <section id="p1">
            <p>This is the first line on the page</p>
            <p>and the second line.</p>
            ...
            <p>1</p>
        </section id="p2">
            ...
        </section>
    </body>
</html>
```

Formally, the above fragment would lead to valid HTML5. However, there are a number of issues with the above fragment. First, there is the use of the section element to mark the original page boundaries. This seems harmless but it a) goes against the way HTML5.2 defines the section element, b) it complicates life for all kinds of consumers of the HTML (like accessibility readers), and c) it makes it technically more difficult to mark up concepts that cross page boundaries. The same arguments hold for the usage of the p element to mark up lines instead of "true" paragraphs. 

The "cross page boundary" argument is shown in more detail below. Suppose there is an Abstract that crosses page boundaries. The following HTML is *not well-formed* and would therefore be rejected by a HTML5 validator:

```html
<section id="p1">
    <div id="myabstract">
        <h1>Abstract</h1>
        <p>The first paragraph of the Abstract</p>
</section>
<section id="p2">
        <p>The second paragraph of the Abstract</p>
    </div>
    ...
</section>
```

The problem is that the div element must be closed before the first section closing tag, and then "restarted" after the second page section start tag. This is clearly very impractical and must be avoided. The same problem occurs when individual lines are wrapped with p or span elements (see the first example). 

*Rule: do not use HTML elements to capture page-model information from the source (PDF; Word; etc.) that was converted into HTML*

specific elements where possible
The p element should not be used when a more specific element is more appropriate.

### alphabetic list of elements 

All elements must be used according to the rules specified in the HTML5 standard, as published by W3C. W3C made the choice to regularly produce new versions of the HTML5 standard. The latest W3C HTML5 Recommendation is (HTML5.2)[https://www.w3.org/TR/html52/]. If and when the next version is published, then Elsevier will use this version. Elsevier will only use W3C specifications that are Recommendations; earlier stages like working draft are not used. 

#### a

#### body

#### div

#### figure

See chapter "figure" below for a description of element figure and its descendants.

#### h*

#### head

#### html

#### li

The (li element)[https://www.w3.org/TR/html52/single-page.html#the-li-element] represents a list item. 

If the parent element is an ol element, then the li element has an ordinal value. This is implicit (see ol element) unless the li element has a value attribute. The value attribute, if present, must be a valid integer giving the ordinal value of the list item.

#### ol

The (ol element)[https://www.w3.org/TR/html52/single-page.html#the-ol-element] represents a list of items, where the items have been intentionally ordered, such that changing the order would change the meaning of the document.

The items of the list are the li element child nodes of the ol element, in tree order.

The default rendering of an ol list is with automatically generated numbers (and dots: 1.; 2.). This implies that a child li element does *not* contain an explicit label. 

*TBD*: policy on @reversed; @start

#### p

The p element represents a paragraph. A paragraph is typically a run of phrasing content that forms a block of text with one or more sentences that discuss a particular topic, as in typography, but can also be used for more general thematic grouping. For instance, an address is also a paragraph, as is a part of a form, a byline, or a stanza in a poem.

A p element cannot have ul, ol, table elements as children. 

#### section

#### span

#### table

See chapter "table" below for a description of element table and its descendants.

#### title

#### ul

The (ul element)[https://www.w3.org/TR/html52/single-page.html#the-ul-element] represents a list of items, where the order of the items is not important — that is, where changing the order would not materially change the meaning of the document.

The default rendering of list items in a ul list is almost always with a hyphen. This hyphen is not explicitly added to the list item - the rendering engine adds the hyphen.

### tables


### figure



