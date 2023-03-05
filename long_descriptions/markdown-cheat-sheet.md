# Markdown Cheat Sheet

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax) and [extended syntax](https://www.markdownguide.org/extended-syntax).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

```markdown
# H1
## H2
### H3
```

### Bold

```markdown
**bold text**
```

### Italic

```markdown
*italicized text*
```

### Blockquote

```markdown
> blockquote
> this is a wonderful quote
```

### Ordered List

```markdown
1. First item
2. Second item
3. Third item
```

### Unordered List

```markdown
- First item
- Second item
- Third item
```

### Code

```markdown
`code`
```

### Horizontal Rule

```markdown
---
```

### Link

```markdown
[Markdown Guide](https://www.markdownguide.org)
```

### Image

```markdown
![alt text](https://www.markdownguide.org/assets/images/tux.png)

```

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

```markdown
| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |
```

### Fenced Code Block

````markdown
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```
````

### Footnote

```markdown
Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.
```

### Heading ID

```markdown
### My Great Heading {#custom-id}
```

### Definition List

```markdown
term
: definition
```

### Strikethrough

```markdown
~~The world is flat.~~
```

### Task List

```markdown
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

## Syntax that does not work in all editors

### Emoji

```markdown
That is so funny! :joy:
```

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight

```markdown
I need to highlight these ==very important words==.
```

### Subscript

```markdown
H~2~O
```

### Superscript

```markdown
X^2^
```
