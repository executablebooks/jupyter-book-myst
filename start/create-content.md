---
title: Writing In MyST Markdown
short_title: Add New Content
subtitle: Use MyST Markdown to author rich narrative and integrate computation.
subject: Quickstart Tutorial
---

:::{important} Objective
The goal of this tutorial is to explore a sample of the ways in which MyST Markdown can be used to create compelling reading experiences, and use the MyST-MD documentation to learn more about MyST.
:::

## Creating a New File

After following [](init.md), our book has some metadata describing its content. Let's now add some content by creating a new file `intro.md`. Here's an example of what you might write:

::::{myst}
# Introduction

I am a book about ... something! Wikipedia has [information about books](wiki:book): hover over the link for more information.

% An admonition containing a note
:::{note}
Books are usually written on paper ... But Jupyter Book can create _websites_!
:::

If you sold 100 books at \$10 per book, you'd have \$1000 dollars according to [](#eq:book). If instead you publish your Jupyter Book to the web for free, you'd have \$0 dollars!

% An arbitrary math equation
:::{math}
:name: eq:book

x \times y = z
:::

Sometimes when reading it is helpful to foster a _tranquil_ environment. The image in [](#fig:mountains) would be a perfect spot!

% A figure of a photograph of some mountains, followed by a caption
:::{figure} https://github.com/rowanc1/pics/blob/main/mountains.png?raw=true
:label: fig:mountains

A photograph of some beautiful mountains to look at whilst reading.
:::

::::

The above "widget" shows both the contents of `intro.md`, and what the underlying MyST-MD engine produces when you build the project as a website. Whilst this is a contrived example, it gives a taste of some of the things you can do with Jupyter Book using MyST Markdown and the MyST-MD engine. For more information on the syntax of MyST Markdown, and the features supported by MyST-MD, see [the MyST-MD authoring documentation](xref:guide/frontmatter).

## Adding to the Table of Contents

Before we can build our project into a webpage or PDF, we should add our new file to the table of contents (TOC). Although the MyST-MD engine is clever enough to find and organise documents in your project folder, using an explicit TOC makes it easier for new contributors to understand the structure of your book. Let's update our [`myst.yml` from the previous section](./init.md#code:myst-yml). Jupyter Book defines a `--write-toc` argument to the `init` command that automatically populates a table of contents from the files MyST-MD finds in the project folder.
:::{code} shell
$ jupyter book init --write-toc
:::
The new `myst.yml` can be see in [](#code:myst-yml-toc).

:::{code} yaml
:filename: myst.yml
:caption: The `myst.yml` produced by running `jupyter book init --write-toc`.
:name: code:myst-yml-toc
:linenos:
:emphasize-lines: 20, 21, 22

# See docs at: https://mystmd.org/guide/frontmatter
version: 1

# Jupyter Book (via myst) base configuration
extends:
- https://jupyterbook.org/myst.1.yaml

project:
  id: 4da9cb15-177c-41f5-8c4e-6a24b4e87eab
  title: An example Jupyter Book
  description: A collection of files that build up a book
  keywords: 
    - jupyter-book
    - something-else
  authors: 
    - name: Jupyter Book
      url: https://jupyterbook.org
  github: executablebooks/jupyter-book
  # To autogenerate a Table of Contents, run "jupyter book init --write-toc"  
  toc:
    # Auto-generated by `myst init --write-toc`
    - file: intro.md
site:
  template: book-theme
  # options:
  #   favicon: favicon.ico
  #   logo: site_logo.png
:::

Now we're ready to [](./build.md).
