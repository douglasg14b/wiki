# How to Contribute

The Forensics Wiki has moved to GitHub, which has required some changes in the
contributing process.

In order to add or update a page, you will need to create or edit a
[Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
file. You can do this in multiple ways, but the general flow is to:

- Copy ("fork") the [Forensics Wiki GitHub project](https://github.com/forensicswiki/wiki)
  - You can then download ("clone") this copy to your computer to work on, or edit
- Make your additions or edits to an article's Markdown file (for example: `plaso.md`)
- Send your changes back to the main Forensics Wiki project for review (submit a "pull request")
- A maintainer will review your changes, request edits if necessary, and once everything looks good, add it to the site ("merge" it)

GitHub has some excellent documentation on [contributing to projects](https://docs.github.com/en/get-started/quickstart/contributing-to-projects)
if you'd like a more detailed explanation.

## Example Using the Command Line

1. Fork the Forensics Wiki project
2. Clone the fork and set Forensics Wiki as the upstream

         git clone https://github.com/[your-github-user-id]/wiki.git

         cd wiki

         git remote add upstream https://github.com/forensicswiki/wiki.git

3. Create a branch for new articles or article updates

         git checkout -b [article-branch-name]

4. Make your changes to the Markdown file(s) and push changes to your repository.

         git push origin [article-branch-name]

5. Create PR for review

<!-- ## TODO: Example Using the GitHub Web UI -->

## Preparing a New Article

### Naming Convention

The file name of the article should be in all lowercase and use underscores to
connect words.  For example, if you write an article around "forensics" then
the name should be `forensics.md`.  If you are writing an article about
"forensic artifacts" then the name should be `forensic_artifacts.md`.

### Content Requirements

In order to make the Forensics Wiki valuable, please use the following
guidelines to help write high-quality articles:

1. _Introduction:_  All articles should have an Introduction, which summarizes what you intend to discuss in the article.
2. _Sections:_  Appropiate sections are used to describe the topic being discussed.  

    For example, if you are writing an article about a tool, you might have the following headings:

    - **Introduction**: This section may include history of the tool, OSes supported, and File Systems supported.

    - **Usage**: This section may include common command line usage and the output to expect.

    - **Use**: This section may include common uses of a tool. A tool could contain one or more common uses. For example, the DD Unix utility could image drives as well wipe drives so data is not recoverable.

    - **See Also**: This section may include links to articles with related content, complementary tools, or forks of the tool. For example, if you were writing an article about The Sleuth Kit (TSK), you may want to include a link to an article about Autopsy.

    - **References**: Any references to support the information you are providing.

    - **External links**: Any external links, such as to the project page or official website.

3. _Media:_ Images are not required, but if they help explain the topic they could be added.
4. _Length:_ There is no requirement for length but the article should be long enough to explain the topic.

### Tags

We are using tags in order to help make content more discoverable.  Tags will appear at the top of the page and should help the user know what the content is related to.  Tags are searchable and clickable, so you could easily see other articles that have the same tag.

### How to Add Tags

After you write your article, you can place tags at the top of the page using the following syntax:

```text
---
tags:
  -  Tools
  -  Windows
  -  Disk Analysis
  -  Commercial Software
---
```

### Tag Guidelines

Tags should describe the content of the article and should be applied uniformly
across all the content.  This will help users discover the content more easily.
 The table below has topics along with possible tags for each topic.  Multiple
topics could apply to one article.  For example, a page tagged with `Tool`
would also likely benefit from a tag denoting the appropriate Operating System,
Software type, and Analysis type.

See examples below the table.

|Topics|Tags|
|-|-|
|Operating Systems| Windows, Linux, macOS, BSD, Unix, Operating System|
|Mobile Operating Systems|Android, iOS, Windows Mobile, BlackberryOS, PalmOS, Symbian|
|Analysis Types| Disk Analysis, File Analysis, Disk Imaging, Data Recovery, Registry Analysis, Log Analysis, Data Carving, Malware Analysis, Secure Deletion, Cell Phone Analysis, System Monitoring, System Analysis, Email Analysis, File System, Network Analysis, Memory Analysis, Memory Imaging, Anti-Forensics |
|Software Type|Open Source Software, Public Domain Software, Commercial Software, Free Software|
|OS Components|OS Component|
|File Types|File Format, Archive, Database, Disk Image, Binary, Audio, Text, Photo|
|Legal|Law|
|Hardware Types|Computer Bus, Microprocessor, Hard Drive, Memory, Personal Device, Write Blockers, GPS|
|People|People|
|Encryption|Encryption, Network Encryption, Disk Encryption|
|Tools|Tools|
|Knowledge|Books, Papers, Reports, Journals, Websites, Blogs, Training|
|Companies / Government|Organizations|
|Mobile|Mobile Networks, Mobile, SIM|

### Tagging Examples

Let's run through some examples to see how we would apply tags to articles.

#### Example 1:  An article about Windows

An article about the Windows operating system in general.

```text
---
tags:
  - Operating System
  - Windows
---
```

#### Example 2:  An article about an open source Linux/macOS tool that parses logs in /var/messages

An article about tools should contain the OSes that it supports (Linux and macOS), what the tool is used for (in this case, Log Analysis), and the software type: Open Source Software.

```text
---
tags:
  - Linux
  - Log Analysis
  - MacOS
  - Open Source Software
  - Tools
---
```

#### Example 3:  An article about Bitlocker encryption

An article about Bitlocker should contain the following tags:

```text
---
tags:
  - Anti-Forensics
  - Encryption
  - Windows
---
```

Bitlocker is a type of `Encryption`, available only for `Windows`, and might be relevant during `Anti-Forensics` analysis.

#### Example 4:  An article about the zip file format

File Types are tagged with File Format and the file type.  In this case, Zip files are Archive files.

```text
---
tags:
  - Archive
  - File Format
---
```

#### Example 5:  An article about Windows System Restore Points

Windows System Restore Points are part of the operating system (`OS Component`) of Windows.

```text
---
tags:
  - OS Component
  - Windows
---
```

### Check Content Formatting

There have been some differences in how certain IDE’s such as Visual Studio code and mkdocs render Markdown.  What this means is that when creating a page in Forensicswiki, some content looks fine in VS code but then once committed to Github the content is not displaying properly.  To ensure content is formatted correctly, you could use a local mkdocs install which has a built in development server.

#### Install mkdocs

Install mkdocs on your system.
```
$ pip3 install mkdocs-material mkdocs-redirects mkdocs-title-casing-plugin
```

#### Run mkdocs

Next, we want mkdocs to load all of the pages of the Forensics Wiki.  Mkdocs needs two things to be able to run and load the Forensics Wiki pages.  

-  It will need a `docs` directory which holds all of Forensics Wiki pages.
-  It will the `mkdocs.yml` configuration file.  This is the configuration that tells mkdocs how to structure the site such as the structure of the menus.  

Both of the previous items are located in the root directory of the repository.  To run mkdocs development server follow the steps below:

1.  Change to the root of the repository.  For example, if you cloned the repository to your home directory.

          cd ~/wiki

2.  mkdocs serve

3.  Open your browser and visit http://127.0.0.1:8000/your_doc_name

### Suggesting New Tags

There might be an article that does not fit well within these tagging
guidelines. If you want to suggest a new tag, please open a
[GitHub Issue](https://github.com/forensicswiki/wiki/issues).
