# Textile Research Papers

The latest Threads Whitepaper release is available at https://docsend.com/view/gu3ywqi

# Setup

```bash
brew install pandoc pandoc-citeproc
```

If you want to do the `Markdown -> LaTeX -> PDF` step below, you'll also want a working LaTeX environment. On MacOS grab it [from here](http://www.tug.org/mactex/) and follow the install instructions. The setup below should use that LaTeX install automatically.

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

We use [pandoc crossref](https://github.com/lierdakil/pandoc-crossref) to do the internal section/fig/equation references, [pandoc citeproc](https://github.com/jgm/citeproc) for the citations. These use a special syntax in the markdown that might be slightly unfamiliar to some. The [docs are pretty good](https://pandoc.org/MANUAL.html#citations), so check those out before making citation or ref changes.

# Export

Building one of the markdown/pandoc formatted papers is relatively simple using the Makefile:

```bash
cd whitepaper
make pdf
```

To generate a pretty-bare bones HTML version:

```bash
pandoc -F pandoc-crossref --citeproc --number-sections index.md -o index.html --mathjax --standalone
```

To generate a workable LaTeX file:

```bash
pandoc -F pandoc-crossref --citeproc --number-sections index.md -o index.tex --standalone
```

To generate a default PDF version via LaTeX:

```bash
pandoc -F pandoc-crossref --citeproc --number-sections index.md -o index.pdf
```
