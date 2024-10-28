# Today I Learned

A Hugo theme focused on simplicity and readability. Ideal for both traditional blog posts and shorter notes that makes
it easy to record and share knowledge that doesn’t need a full blog post. Perfect for quick tips, insights, and
discoveries.

Check out the theme demo at <https://michenriksen.com/til-example-site>.

## Features

### Content graph view

Visualize connections between notes and posts like seen in Apps like Obsidian. The content graph provides a web of your
knowledge, letting you and your readers explore related notes and see how everything connects.

### Side notes

Add side notes that sit neatly alongside your main content. Perfect for extra details, tips, or fun facts without
breaking up the flow of your writing.

### Admonitions

Highlight important notes, warnings, tips, or anything that deserves special attention with styled callout boxes. Great
for keeping readers informed.

### Improved JSON-LD data

The theme enhances Hugo’s built-in [JSON-LD] structured data by adding more detailed metadata, helping search engines
better understand your content and making it easier for your posts to appear in relevant search results.

### Built-in blocking of generative AI/LLM associated web crawlers

If you’re concerned about your content being used as training data for generative AI and language models, the theme’s
robots.txt template allows you to easily block a wide range of genAI and LLM-related web crawlers.

### Easy Creative Commons licensing

The theme includes simple options for adding a [Creative Commons license] to your content, allowing you to define how
others can use, share, or adapt your work. You can choose the most appropriate Creative Commons license, and it will
automatically appear in the website footer with optional usage icons.

## Configuration

The theme offers a few configuration options for customizing the look and behavior. These options should be declared
in the `[params]` section of your site's [hugo.toml] configuration file.

```toml
[params]
  # Set how dates should appear across the site.
  # For format options, visit https://gohugo.io/functions/time/format/
  # Default: :date_long
  dateFormat = ':date_long'

  # Show content graph for single notes and posts.
  # Default: true
  showGraph = true

  # Author details for the JSON-LD structured data.
  [params.author]
    name = 'John Doe'
    email = 'johndoe@example.com'

  # Homepage setup
  [params.home]
    # Display recent blog posts on the homepage.
    # Default: true
    showRecentPosts = true

    # Set how many recent blog posts to show.
    # Default: 3
    recentPostsLimit = 3

    # Display recent notes on the homepage.
    # Default: true
    showRecentNotes = true

    # Set how many recent notes to show.
    # Default: 5
    recentNotesLimit = 5

  # Notes page setup
  [params.notes]
    # Set the number of notes to list on each page.
    # Default: 20
    pageSize = 20

    # Show a filter option for note categories above the notes list.
    # Default: true
    showCategoryFilter = true

  # Footer setup
  [params.footer]
    # Specify the Creative Commons license to apply to your content.
    # Options: `by`, `by_sa`, `by_nc`, `by_nc_sa`, `by_nd`, `by_nc_nd`, `zero`, `none`
    # Learn more at https://creativecommons.org/share-your-work/cclicenses/
    # Default: none
    creativeCommonsLicense = 'none'

    # Show Creative Commons icons for the selected license.
    # Default: true
    showCreativeCommonsIcons = true

    # Show a credit link to the Today I Learned theme in the footer.
    # Default: true
    showThemeCredit = true

  # robots.txt setup
  [params.robotstxt]
    # Block CommonCrawl from indexing your site. CommonCrawl data is often used to train AI models.
    # Learn more at https://commoncrawl.org/ccbot
    # Default: false
    blockCC = false

    # Block various crawlers associated with AI and machine learning model training.
    # Crawler list from https://github.com/ai-robots-txt/ai.robots.txt
    # Default: false
    blockAI = false
```

[JSON-LD]: https://json-ld.org/
[hugo.toml]: https://gohugo.io/getting-started/configuration/#configuration-file
[Creative Commons license]: https://creativecommons.org/share-your-work/cclicenses/
