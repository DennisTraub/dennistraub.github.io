---
draft: false
date: 2024-10-31T09:31:51+01:00
title: How to set up the vertical ruler in VS Code
categories: [tips, tools, ide, vscode]
isNote: true
---

There's this handy vertical ruler feature in most IDEs, showing a simple guide line to help maintain consistent line lengths across your codebase. It's one of those small tools that makes a big difference in keeping your code maintainable and easier to review.

Here's how to set it up in VS Code: Open your [settings file](https://code.visualstudio.com/docs/getstarted/settings) and add the `editor.rulers` configuration. You can set a single ruler at the traditional 80-character mark, or add multiple guides for different contexts. Here's an example that sets the ruler at 80 characters:

```json
    "editor.rulers": [80]
```

Remember, this ruler is just a visual guide - you'll still need to format your code manually or with your preferred auto-formatter.