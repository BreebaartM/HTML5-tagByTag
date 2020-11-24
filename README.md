# README.md for normalized.html

## normalized.html

- are line numbers really integral to the message that the author is trying to convey? 
    - No, they are useful when editing / reviewing but are left out after that phase
        - remove any span / p related to line numbering
- should everything have a span?
    - No, only when it is directly adding information (which means: almost never!)
    - example: do not put a span around a line (typewriter style)
- do I need to put an @id on everything
    - No, only when it can be reasonably expected that it will be targetted
    - example: no need to put @id on sup, sub, etc.
- p elements must *not* be used to emulate typewriter style line ends
- section elements must *not* be used to delineate page boundaries
- it is valuable to have internal links coded as internal links
    - see example link from text to reference section
- no CSS embedded in the document
    - unless it is *really* tied to the content
    - e.g. anything related to capture of page semantics in source should not remain
- algorithm for chosing sup/sub and span does not work properly
    - author info: 2nd line goes from sup to span
    - similar problem in abstract

## layout.json

- it makes no sense whatsoever to treat this as a graph
- logic behind pp:insertion seems doubtful, but it does point to a more generic mechanism for pointing into HTML without polluting it (with countless span elements)

## style.css

- this is the style of the *source* document
- it makes more sense to merge this info into one file: e.g. source.json that captures source material specifics (combining elements of layout and style)

