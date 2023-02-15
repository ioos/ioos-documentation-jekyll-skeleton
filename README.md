# ioos-documentation-jekyll-skeleton

A template/skeleton repository that can be used as a starting point to create a new IOOS GitHub Documentation Site at https://ioos.github.io/.

## Getting Started

See online instructions for working with this repository at: https://ioos.github.io/ioos-documentation-jekyll-skeleton/howto.html 

## Deploying site locally
Requirements:
* bundle
* Jekyll

_Note: Replace `your-documentation-repo-name` with the name of your repository (eg. `ioos-documentation-jekyll-skeleton` for this repository._

Clone this repository:
```commandline
git clone https://github.com/ioos/your-documentation-repo-name.git
```
To build the site, in the `your-documentation-repo-name/` directory run:
```commandline
bundle exec jekyll serve --config _config.yml --watch --verbose --incremental
```
This will deploy a website at: http://127.0.0.1:4000/your-documentation-repo-name/

Make edits to the appropriate markdown files in `_docs/`. 

If changing headers and menus, stop the running server by entering `ctrl-c` in the terminal. Then run:
```commandline
bundle exec jekyll clean
```
Then build the site again.
```commandline
bundle exec jekyll serve --config _config.yml --watch --verbose --incremental
```
And review at http://127.0.0.1:4000/your-documentation-repo-name/

## IOOS Documentation Site: ___________

Fill in the details as appropriate for the new documentation site you create from the skeleton, and delete the instructions above.

**Site URL:** https://ioos.github.io/your-documentation-repo-name

