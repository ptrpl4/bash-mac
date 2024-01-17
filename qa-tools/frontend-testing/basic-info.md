# Basic info

### Locators

#### CSS selectors

Allow you to select elements on a page based on their styles and structure. \
Can be simple (by tag, class, identifier) or complex (with a combination of conditions).

#### XPath

A query language for selecting elements in XML documents such as HTML pages. It provides extensive capabilities for precise element retrieval. Among other things, it allows you to access a parent element through a child element.

**Absolute path** - starts from the root element and specifies the full path to the target element.&#x20;

`/html/body/div[1]/form/input`

**Relative path** - starts from the current context and is more flexible than absolute paths.&#x20;

Relative expressions start with a double slash (`//`).&#x20;

`//div[@class='container']//button`

#### Identifiers (ID)

A unique number (name) that can be used as a locator. \
Identifiers are usually the most stable locators.

#### Classes and attributes&#x20;

However, classes can be repetitive and changes to the page structure can affect the locator.

#### Conclusion

1. Use ID if the element has a unique identifier.&#x20;
2. Use Name when elements have unique names, especially in forms.&#x20;
3. Use XPath when there are no unique IDs or names and you want to select items based on their structure, text, or other attributes.

\---
