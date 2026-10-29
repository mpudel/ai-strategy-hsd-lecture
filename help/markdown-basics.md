# Markdown Basics

Markdown is a simple markup language for formatting text. You write plain text and add a few special characters -- the editor does the rest.

Here are the most important markers, first raw (how you write them) and below that how they are displayed

## Headings

```markdown
# Heading 1 (largest)
## Heading 2
### Heading 3
```

# Heading 1 (largest)
## Heading 2
### Heading 3


## Text formatting

```markdown
**bold**
*italic*
~~strikethrough~~
`inline code`
```

**bold**, *italic*, ~~strikethrough~~, `inline code`

## Lists

**Bullets:**
```markdown
- Item 1
- Item 2
  - Sub-item
```

- Item 1
- Item 2
	- Sub-item

**Numbered:**
```markdown
1. First item
2. Second item
3. Third item
```

1. First item
2. Second item
3. Third item

## Links and images

```markdown
[[setup-guide]]
[Link text](https://example.com)
![Image description](image.png)
```

[[setup-guide]]
[codecentric AG](https://www.codecentric.de)


## Code blocks

Three backticks for multi-line code:

````markdown
```python
print("Hello world")
```
````

```python
print("Hello world")
```


## Quotes

```markdown
> This is a quote.
> It can span several lines.
```

> This is a quote.
> It can span several lines.

## Tables

```markdown
| Column 1 | Column 2 |
|----------|----------|
| Value A  | Value B  |
| Value C  | Value D  |
```

| Column 1 | Column 2 |
|----------|----------|
| Value A  | Value B  |
| Value C  | Value D  |

## Horizontal rule

```markdown
---
```


---

## Checklists

```markdown
- [ ] Open task
- [x] Done task
```

- [ ] Open task
- [x] Done task

---

**Tip:** You don't have to memorize everything. Just start writing -- the most important formatting (`#`, `**`, `-`) covers 90% of cases.
