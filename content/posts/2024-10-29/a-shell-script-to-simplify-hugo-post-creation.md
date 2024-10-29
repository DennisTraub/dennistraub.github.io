---
date: '2024-10-29T11:05:33+01:00'
title: 'How I simplified Hugo blog post creation (with a little help from AI)'
summary: "Here's how I turned my cumbersome six-step Hugo post creation process into a single command using a shell script - with [Amazon Q Developer](https://aws.amazon.com/developer/generative-ai/amazon-q/?trk=bddf5c60-e524-4fac-be77-9847d064e1a7&sc_channel=el) doing the heavy lifting. A quick win for lazy developers like me, who'd rather focus on writing than remembering dates and fiddling with filenames."
description: How I automated Hugo's 'hugo new posts/[file-name].md' command into a simple shell script that handles dates and filenames. Created with Amazon Q Developer, because who wants to type dates and deal with dashes manually?
draft: false
categories: ["shell-scripting", "amazon q developer"]
---

## The problem with creating Hugo posts

I wrote this little script to simplify creating new posts in this blog. Well, actually [Amazon Q Developer](https://aws.amazon.com/developer/generative-ai/amazon-q/?trk=bddf5c60-e524-4fac-be77-9847d064e1a7&sc_channel=el) wrote it - I just asked nicely, checked for errors, and tweaked the result a little.

If you're new to Hugo like me, you probably know you create posts by running:

```shell
hugo new posts/[file-name].md
```

Simple enough, right? Well, there are a few things that make this more cumbersome than it needs to be:

1. I like to organize my posts by date (e.g., `posts/2024-10-29/`), but I never seem to remember today's date.
2. As far as I know, post filenames can't have spaces, so I have to manually convert "My title" to `my-title-with-dashes` - sure, maybe camelCase works too, but that's even more mental overhead.
3. I constantly forget to add the `.md` extension at the end.

## The manual workflow
So my typical workflow looks like this:

1. Type `hugo new posts/`
2. Stop to look up today's date
3. Continue with `2024-10-29/title-with-dashes`
4. Hit enter
5. Realize I forgot the `.md` extension (again!)
6. Rename the file to `posts/2024-10-29/title-with-dashes.md`

_Now, I should mention that Hugo is a great framework with a huge community, so there's probably a better way to do this. But as a newbie, this is what I found in the docs, and these are the pain points I ran into._

## The solution
Six steps just to create a new post? I'm a lazy developer, so I knew there had to be a better way. Here's the shell script I now use from my project's root folder:

```shell
> ./new "new title"
Executing: hugo new posts/2024-10-29/new-title.md
Content: "./content/posts/2024-10-29/new-title.md" created
```

And here's how it works:

```shell
#!/bin/sh

# Check if a title was provided
if [ $# -eq 0 ]; then
    echo "Usage: new \"[title]\""
    exit 1
fi

# Get the title from the command line argument
title="$1"

# Generate the current date in YYYY-MM-DD format
date=$(date +"%Y-%m-%d")

# Convert the title to lowercase and replace spaces with dashes
formatted_title=$(echo "$title" | tr '[:upper:]' '[:lower:]' | tr ' ' '-')

# Create the Hugo command
hugo_command="hugo new posts/$date/$formatted_title.md"

echo "Executing: $hugo_command"

# Execute the Hugo command
$hugo_command
```

## Behind the scenes: The AI assistant
Remember that part where I said [Amazon Q Developer](https://aws.amazon.com/developer/generative-ai/amazon-q/?trk=bddf5c60-e524-4fac-be77-9847d064e1a7&sc_channel=el) wrote this? Here's how that actually went down. I literally just opened Q's chat in my IDE and had this conversation:

**Me:**

Create a shell script that turns:
```
./new "[title]"
 ```
into: 
```
hugo new posts/[date (format: YYYY-MM-DD)]/[title-with-dashes].md
```


Example: Today is October 29th, 2024. When I run `./new "my title"`, execute `hugo new post/2024-10-29/my-title.md`

**Amazon Q Developer:**

Certainly! I'll create a shell script named `new` that accomplishes what you've described. Here's the script:

```shell
/* Script omitted. It's almost the same as above ↑ */
```

To use this script:

1. Save it in a file named `new` (without any extension) in the root directory of your project. 
2. Make the script executable by running:
   ```shell
   chmod +x /path/to/new
   ```
3. Now you can use the script as you described. For example:
   ```shell
   new "My title"
   ```
This script does the following:
1. It checks if a title was provided as an argument.
2. It gets the current date in the YYYY-MM-DD format.
3. It converts the provided title to lowercase and replaces spaces with dashes.
4. It constructs the Hugo command with the formatted date and title.
5. It executes the Hugo command to create the new post.

With this script, when you run `new "My title"` on October 29th, 2024, it will execute:

```shell
hugo new posts/2024-10-29/my-title.md
```

Remember to ensure that you save this script in the root folder of your project so that it creates new posts in the correct location.

---

And that was it! Kind of feels like cheating, right? But the script works exactly as I wanted it to, and I'd probably have written something similar myself - just with more trial and error, visits to Stack Overflow, and time spent looking up shell commands I don't use often enough to remember.