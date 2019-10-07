# Setup

```bash
brew install pandoc pandoc-crossref pandoc-citeproc
```

# Develop

You'll probably also want to use VSCode with the [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced) plugin.

You'll want to use the following settings:

```json
{
    "markdown-preview-enhanced.enableTypographer": true,
    "markdown-preview-enhanced.breakOnSingleNewLine": false,
    "markdown-preview-enhanced.usePandocParser": true,
    "markdown-preview-enhanced.pandocMarkdownFlavor": "markdown-raw_tex+tex_math_dollars+fenced_code_attributes+backtick_code_blocks",
    "markdown-preview-enhanced.pandocArguments": "--number-sections,--filter=pandoc-crossref",
    "markdown-preview-enhanced.mathRenderingOption": "MathJax",
    "markdown-preview-enhanced.codeBlockTheme": "auto.css",
    "markdown-preview-enhanced.enableEmojiSyntax": false
}
```

# Export

To generate a pretty-bare bones HTML version:

```bash
pandoc -F pandoc-crossref -F pandoc-citeproc --number-sections draft.md -o draft.html --mathjax --standalone 
```

To generate a default PDF version via LaTeX:

```bash
pandoc -F pandoc-crossref -F pandoc-citeproc --number-sections draft.md -o blah.pdf
```
