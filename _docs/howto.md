---
title: Getting started with IOOS Jekyll Documentation Theme Skeleton
keywords: sample homepage
tags: [getting_started, about, overview]
toc: false
search: exclude
#permalink: index.html
summary: Instructions to create a new IOOS GitHub documentation site based on the 'ioos-documentation-jekll-skeleton' repository.
---


## Background

The [ioos-documentation-jekll-skeleton](https://github.com/ioos/ioos-documentation-jekyll-skeleton) repository is a template, or 'skeleton' starting point to create a new GitHub-based documentation site that uses the IOOS [documentation-theme-jekyll](https://github.com/ioos/documentation-theme-jekyll).

The instructions below will allow you to create a new GitHub Pages site that follows the look and feel/functionality of the Jekyll documentation theme used by the [https://ioos.github.io](https://ioos.github.io) documentation site, resulting in a blank slate site to which you can add your own content.


## Getting Started

### Step 1: Fork and download the ioos-documentation-jekyll-skeleton repository

This is done on the GitHub website.  These steps assume you already have a GitHub account in place.

1. Browse to the [ioos-documentation-jekyll-skeleton](https://github.com/ioos/ioos-documentation-jekyll-skeleton) repository, and 'fork' the repository to your own user account: ![GitHub fork example image](https://ioos.github.io/fork.png){:style="width: 400px; display:block;"}

2. Rename your forked repository as desired via the GitHub website (by default, it will retain the same 'ioos-documentation-jekyll-skeleton' name as the repository it was forked from).  The repository name ideally should reflect the content to be published therein.  IOOS uses hyphens to separate names in documentation repositories (e.g. my-new-documentation-repo).  At the end of this step, you should have a new repository available at the following URL: https://github.com/\<github_username\>/\<my-new-documentation-repo\>.

3. Download or 'clone' the repository to edit it on your local machine.  This step assumes you have a git client installed, which is beyond the scope of these instructions.  For those who do not have git, the editing steps can be accomplished on the GitHub website one file at a time (see Step 2 for details).  ![GitHub clone example image](https://ioos.github.io/clone.png){:style="width: 400px; display:block;"}

 
4. Continue to Step 2 to begin editing content in your new fork.


### Step 2: Edit your documentation site content

Editing content in your new fork of the documentation skeleton repository can be done in one of two ways:
1. Locally using a text editor, and optionally running in local development mode via a Ruby/Jekyll installation
1. Online using the GitHub website

Editing locally is easier for making major changes to the site, including more complicated steps like modifying the sidebar layout, working with images, etc.  It requires a working git client to transmit changes back to your GitHub fork for rendering online, as well as a local installation of Ruby/Jekyll to preview your changes.  Instructions for setting up the Ruby/Jekyll environment can be found in the original Jekyll Documentation Theme [instructions](https://idratherbewriting.com/documentation-theme-jekyll/index.html) - also see the [Local Development With Jekyll](#local-development-with-jekyll) section for more details.

Editing in GitHub is easier for more minor content modifications (see the Notes section below).

The important files and directories to modify in the template are the following:

|**Name**|**Description**|
|--------|------------|
|**\_config.yml** | Main Jekyll configuration files.  Modify settings in these to change anything related to the theme.  The important settings to update are primarily located at the top of the file, and include settings like: 'title', 'name', 'description', 'baseurl', among others.  More documentation can be found in the 'Documentation Theme for Jekyll' original documentation (see below).|
|**/\_data/sidebars/sidebar_ioos.yml**| Configuration file for a side accordion navigation menu.  Further description of the configuration details and how they work is beyond the scope here, refer to the Jekyll and the 'Documentation Theme for Jekyll' original documentation for more info.|
|**/\_docs/**| Directory to place any GitHub-standard markdown (.md) content to publish.|
|**/\_docs/index.md**| The markdown file that contains the content for the 'homepage' (index.html) for the site - this should be updated/replaced accordingly.|
|**/\_docs/images/**| A folder to add any image content to reference in your documentation pages.|

**Notes:** 
- All published documents in Markdown must be placed into the '_docs' directory, where they can be edited with any true text editor such as 'vi', 'emacs', 'notepad', 'notepad++', etc.  

- Alternatively,  if you just need to edit a document or two on the existing site, you may do that directly on GitHub with your browser in 3 simple steps:
   1. Go to the page you want to edit, and click on the "Edit me" button just below the page Title and Summary;
   2. Open it for editing by clicking on the "pencil" icon at the right side above the file content;
   3. Make all changes, preview them to make sure that everything is OK, and commit them to the 'gh-pages' (make sure that the "Commit directly to the gh-pages branch" option is checked).


## Local Development with Jekyll

As noted above, more complex changes to theme content such as configuring the sidebar navigation, working with images in the `/_docs/images/` folder, or larger edits to the text content are more easily made by installing the dependencies to run Jekyll (the Ruby programming language, primarily) and editing files in a text editor for preview.  This allows instantaneous rendering of the site exactly as it will appear in GitHub pages so you can more rapidly iterate changes.  You can then use a git client to make commits to your fork of this skeleton repo once you're happy with your changes, and push them to GitHub.

Full instructions on setting up a local Jekyll development environment are available in the original Jekyll Documentation Theme [instructions](https://idratherbewriting.com/documentation-theme-jekyll/index.html).  Follwing are some useful Jekyll commands to run once the installation procedures are completed and your environment is configured.


Run Jeyll via Bundler in incremental build, verbose logging mode (using the `_config_dev.yml` for local development settings):
```
bundle exec jekyll serve --config _config.yml,_config_dev.yml --watch --verbose --incremental
```

Clean the locally-built Jekyll site (necessary to render changes to sidebar and top menu components):
```
bundle exec jekyll clean
```

By default, the `bundle exec jekyll serve` command will serve the site on your machine at: 

[http://localhost:4000/ioos-documentation-jekyll-skeleton/](http://localhost:4000/ioos-documentation-jekyll-skeleton/)

You can modify the path to match your forked repository name by making edits to the `_config_dev.yml` file. 


## Configuring the Side Navigation Bar

The sidebar navigation adapts to the documentation. Although the theme allows to use several sidebars (see `_config.yml` file), a single sidebar 'ioos_sidebar' is used by default for IOOS' implementation. The sidebar name must be specified either in the `_config.yml` in the 'defaults' section (as it is in this skeleton repo), or it may be configured on a page-by-page basis in the page's frontmatter. Here's an example of the page frontmatter showing the sidebar property:

```
---
title: Alerts
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "You can insert notes, tips, warnings, and important alerts in your content. These notes are stored as shortcodes made available through the linksrefs.hmtl include."
sidebar: ioos_sidebar
permalink: mydoc_alerts
---
```

The `sidebar: ioos_sidebar` refers to the `_data/sidebars/ioos_sidebar.yml` file. The sidebar data file uses a specific YAML syntax that you must follow. Follow the sample pattern shown in the theme, specically looking at `ioos_sidebar.yml` as an example.

For more details on the sidebar syntax, see [Sidebar navigation](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_sidebar_navigation.html).




## Editing Markdown Documents

This theme uses a Kramdown variety of the Markdown - a lightweight markup language with plain text formatting syntax. The Kramdown is a superset of Markdown that supports standard Markdown and various extensions. The GitHub Pages naturally support rendering documents in Kramdown through the GitHub Jekyll implementation. The detailed description of the Kramdown syntax can be found by following the links in the Reference section below.

Every document must start with the so-called frontmatter properties:

```
---
title: "Some title"
tags: [sample1, sample2]
keywords: keyword1, keyword2, keyword3
last_updated: Month day, year
summary: "optional summary here"
sidebar: sidebarname
topnav: topnavname
toc: false
#search: exclude
#permalink: filename.html
---
```

For titles, surrounding the title in quotes is optional, but if you have a colon in the title, you must surround the title with quotation marks. If you have a quotation mark inside the title, escape it first with a backlash `\`.

Values for `keywords` get populated into the metadata of the page for SEO.

Values for `tags` must be defined in your `_data/tags.yml` list. You also need a corresponding tag file inside the tags folder that follows the same pattern as the other tag files shown in the tags folder. (Jekyll won't auto-create these tag files.)

In the current version of the theme, the `permalink` property value interferes with other collection settings; therefore it should be commented in the frontmatter. However, it should not be removed as it may be needed in future versions.

Value for `search` controls inclusion of the document content into theme search mechanism. If you want to be able to perform basic search through your site documents, make sure that this property is commented in the frontmatter.

Follow the sample pattern shown in the theme, specifically looking at Markdown sample documents in the `_docs` folder as an example.


## A Note on Submodules  

This theme uses two GitHub 'submodules'.  Submodules are essentially links to other GitHub repositories that allow certain components of the site to be synchrnonized more easily across all of IOOS' GitHub Pages [https://ioos.github.io](https://ioos.github.io) documentation sites.

For example, the menu bar at the top of the page is configured within a submodule, as is the look and feel of the theme.  These details aren't critical for most general-purpose users of this skeleton repo, however, periodically you may need to update the submodules if the upstream content changes so your fork can be in alignment with the other IOOS documentation sites (or an IOOS admin may do this step for you if your documentation site is deployed alongside the other IOOS GitHub documentation pages).

The git submodules for this skeleton repository are found in these subdirectories:

|**Submodule Path**|**Description**|
|--------|------------|
|**/_data/navbars_theme/**| the YAML configuration file for the IOOS top navigation bar (`topnav_ioos.yml`) and other files|
|**/theme/**| the Jekyll theme files containing the look and feel and functionality of the site - sourced from the [ioos/documentation-theme-jekyll](https://github.com/ioos/documentation-theme-jekyll) repo|

If you have a git client installed, you can pull in upstream changes in these submodules by running the following:

```
 git submodule update --remote --merge
```

## References  

 - [Original Documentation for the Documentation Theme for Jekyll](http://idratherbewriting.com/documentation-theme-jekyll/index.html)
   - [Ruby & Jekyll Installation and Setup Section](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_about_ruby_gems_etc.html)
 - [A Comprehensive Guide for Jekyll](https://jekyllrb.com/docs/)
 - [Ruby documentation & downloads](https://www.ruby-lang.org/en/)
    - [Ruby Installer for Windows](http://rubyinstaller.org/downloads/)
    - [A Guide on Ruby Installation and Setup for Windows 10](https://www.digitalocean.com/community/tutorials/how-to-install-ruby-and-set-up-a-local-programming-environment-on-windows-10)
 - [General information on the way GitHub uses Jekyll in 'GitHub Pages' sites](https://help.github.com/articles/about-github-pages-and-jekyll/)
    - [In particular, how to use a specially-named branch 'gh-pages' to push documentation for a 'Project' page (which most repos will fall under)](https://help.github.com/articles/user-organization-and-project-pages/)
 - GitHub Kramdown:
    - [Kramdown Syntax](https://kramdown.gettalong.org/syntax.html)
    - [Kramdown Quick Reference](https://kramdown.gettalong.org/quickref.html)
