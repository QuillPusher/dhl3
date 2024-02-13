# CR Website Template

This is a template website based on this open source [project](https://github.com/YaleDHLab/dhlab-site).

## Site Contribution User Guide

Folder structure:

### _about

The `past_associates.html` file includes liquid placeholders to pull values from `_includes/about/personnel_archive.html`, which iterates over values in respective YML files in the `_data` folder.

### _awards

Markdowns in this folder are iterated, and the `title` attribute in each file is used by the `_includes\header\header.hmtl` file to create a specific list of nested dropdown menu in one of the top level navigation menu.

### _data

Includes several Yaml files that other pages iterate over. It also includes a `schema` file for various Jekyll collections (team, events, news, etc.) and a `taxonomy` file (probably used in search/indexing).

### _events

The Events Collection includes a markdown file for each Event:

- shown in events widgets on homepage (one for each Catergory tag: Meetup, Talk & Workshop), and 

- listed on `events.html` page.

### _includes

Includes several code snippets that can be included in  other pages. Examples:

```
<figure>
   <a href="{{ include.url }}">
   <img src="{{ include.file }}" style="max-width: {{ include.max-width }};"
      alt="{{ include.alt }}"/>
   </a>
   <figcaption>{{ include.caption }}</figcaption>
</figure>
```

### _includes\about

Liquid/HTML code to create a contact card for current or past team members (team_member, personnel_list, personnel_archive, and exec_committee_archive).

### _includes\awards

Formats to display grants, scholarships, projects, etc.

### _includes\cards

Different Card Layouts (desktop, mobile, etc.) to display items in a collections (News, Events, etc.), for example on the main page.

### _includes\events

Small elements (date, time, and metadata) that are utilized in cards, etc. when displaying an event.

### _includes\grids

Different grid layouts (columns and boxes) that can be utilized when displaying different grids, cards, images, etc.

### _includes\header

- header.html: includes main menu code (can rename menu items here).

- header_links.html: generates page links for header menu items.

- header_logo.html: Points to the two logo SVG images.

- header_search.html: Search Text Field and Trigger button shown after clicking Search icon.

- navicon.html: Renders the image/drawing of the Hamburger Menu button for mobile view.

### _includes\heroes

- captioned_hero.html: Liquid/HTML code to render Hero (top banner) Image/video

- hero_video.html: Mute and infinitely loop the linked video banner (hosted on DH lab's AWS cloud account).

- mobile_hero.html: renders Mobile hero/background image.

### _includes\json

Creates JSONs out of iterated items (date, title, url, etc.).

### _includes\news

Different layouts to fetch and display news articles (markdowns), for example on the main page.

### _includes\projects

- team_members.html: Iterate over team members related to a specific project.

### _includes\resources

- workshops.html: Iterate and list/render events (markdowns in `_events`) of the workshop category:

```
---
categories:
  - Workshop
---
```

### includes\sidebars

Various side bar layouts that can be added to any page.

### _includes\social_media

Links and icons to share current page on social media (Twitter, Instagram, and Clipboard).

### _includes\text

Different text layouts (e.g., right column text, left column text) that are reused in several pages.

### _includes (other includes)

- allbooks.html: Bookshelf page layout.

- analytics.html: Add Google Analytics configuration/key string here.

- curated-shelf.html: another bookshelf

- filters.html: Filter tags and categories.

- footer.html: Most things showing in the universal footer (white logo, address, mailto, partenets, subscribe, etc.) can be configured here.

- get_filtered_records.liquid: Filter a list of records by a specific category.

- get_future_or_past_records.liquid: Filter a list of records by a specific category and additional conditions.

- get_sorted_records.liquid: Sort a list of records by a specific category.

- head.html: head section of HTML documents, which includes metadata, links to stylesheets, google-site-verificatio, etc.

- simple.html: This is the layout for all single page articles after you click an Event/News/Project link. It is a simplified page layout/ single article view (for single news, event, and project articles (from markdown files)), that conditionally shows content, images and metadata. Also shows 3 related articles at the bottom of the page. 

- warning_banner.html: Shows a warning message banner if configured on the main `index.html` page.

### _layouts

Page layouts that can be used to render pages in a specific way (news, event, etc.). Most layouts take `default.html' as a parent and use a new class name to help differentiate themselves from others. Example:

```
---
layout: default
class: news-detail-page simple-page
---
```

### _news

This is where News Collection's Article Markdown files are placed.

### _plugins

Installed Ruby plugins.

### _projects

This is where Project Collection's Article Markdown files are placed.

### _resources

This is where Other Resources Collection's Article Markdown files (e.g., consultations, etc.) are placed.

### _site

Jekyll produced the Static Site in this folder. This folder is ignored while pushing the repository to github and the GitHub Actions generate the static site artifacts using a job on each commit on the server.

### _team

This is where Team Collection's Article Markdown files are placed. Former teammates are placed in its sub-directory.

### _templates

Includes some random templates to help create new markdown files (news, events, etc.) quickly.

### assets

Includes assets like CSS, JavaScripts, Fonts, Images, PDFs, etc.

### assets\js

Includes the moving parts of the website through various javascripts, including Search, Navigation, Google Tag Manager, etc. Note that these require dependencies to be installed on the site folder (as discussed in "Setting up a Local Development Environment" section below) before development work is started locally.

### node_modules

Node.js modules (e.g., babel) required for some features are stored here.

### tests

Unit tests to run before deployment (required if you deploy using `npm run deploy` to remote severs like AWS, etc. )

### utils

Python utilities for tasks like resizing images, uploading to AWS cloud (where the DH Lab original site is deployed), scrape past articles, reformat dates to rename files, etc.


### _config.yml 

Main configuration file for the static site (other dev/production config files are useful for testing/staging). Following changes are required to support Github Pages:

```
baseurl: '/reponame'
url: yourgithubname.github.io
dependencies:
  - gem: github-pages
    version: '~> 228'
```

### Gem File

Following changes are required to support Github Pages:

```
#gem "jekyll", "~> 4.3"
gem "github-pages", "~> 228", group: :jekyll_plugins
```

### package.json

Used in Node.js projects to define the project's metadata and dependencies. 

### CNAME

Used to specify a custom domain name for the site. 

### index.html

Site's home page.

### sitemap.xml

Used by search engines to index the pages of the site.

### webpack.config.js

Configuration file for a JavaScript project used by Webpack to bundle the project's assets into a single file for deployment. It includes plugins for optimization, etc.


### yarn.lock

Autogenerated file that is created after installing Yarn for Javascript Dependencies (as shown in "Setting up a Local Development Environment" steps below).

> End of Site Contribution User Guide

  <hr />

## Setting up a Local Development Environment

First download the application source:

```
git clone https://github.com/YaleDHLab/dhlab-site
cd dhlab-site
```

### Mac Users
Follow [these instructions](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#start-here-if-you-choose-the-long-and-manual-route) to ensure modern, non-System ruby on recent versions of OS X, especially on Apple Silicon (M1 chips).

Pay special attention to the section where you [detect, and if neccessary remove](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#start-here-if-you-choose-the-long-and-manual-route), previous ruby virtual environments such as rvm, rbenv, and asdf.

Then:
```
brew install chruby ruby-install
ruby-install ruby-2.7.2
echo ". /usr/local/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo ". /usr/local/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-2.7.2" >> ~/.zshrc
```
Important: close and reopen the Terminal.app (all windows, not just your current one).
Verify you're on the right version of Ruby:
```
ruby -v
```
Then install the Ruby dependencies:

```
bundle install
```
On the Mac, use homebrew to install Node:
```
brew install node
```
Then install yarn and install the JavaScript dependencies:

```
npm install -g yarn
yarn install
```

Finally, you can start the development server by running:

```
bundle exec jekyll serve --incremental
```

### Windows Users

> Disclaimer: Following steps for Windows are not fully functional, as discussed in [this issue](https://github.com/YaleDHLab/dhlab-site/issues/924).

- Install ruby-2.7.2 ([downloads lnk](https://rubyinstaller.org/downloads/archives/))
- On the last step, select "Install MSYS2 and Mingw". If it fails to do so automatically, then follow the next two steps, else skip them.
  - install MSYS2 manually since ruby installer script failed to do it automatically ([download link](https://www.msys2.org/#installation))
  - install Mingw using MSYS2 terminal (`pacman -S mingw-w64-ucrt-x86_64-gcc`)
- install Node.js ([download link](https://nodejs.org/en/download))
-  install yarn and install the JavaScript dependencies
```
npm install -g yarn
yarn install
```

- add gh-pages support to autobuild site on every commit (this removes the need to use 'npm run deploy' step suggested in Mac Users section, since Github Pages are auto created this way on each commit)

gem file:
```
#gem "jekyll", "~> 4.3"
gem "github-pages", "~> 228", group: :jekyll_plugins
```
config.yml
```
baseurl: '/reponame/'
url: yourgithubid.github.io
dependencies:
  - gem: github-pages
    version: '~> 228'
```

- Install/update bundles after changes in Gem file and then user 'serve' to view it on localhost:

```
bundle update
bundle exec jekyll serve --incremental
```

### Repo Settings to Enable GitHub Pages

- on Github web, change repo settings to enable GitHub Pages website (Settings > Pages > Build and deployment > Deploy from a Branch > master/root)

- If this is other than a branch named "master", then it may need to be defined in the 'Environments > github-pages' setting for your repository.

- Commit updated files to repo

- Site should be live at https://yourgithubid.github.io/reponame/

**Screenshot (dependencies installed)**

<img width="960" alt="node" src="https://github.com/YaleDHLab/dhlab-site/assets/130300172/ae00a327-cf35-4dc3-8239-b59651eba794">


## Deployment

To deploy the site to GitHub pages you can run:

```
npm run deploy
```

> Note: This step is only required if you're using the Python utility `utils\upload.py`. Sites can be auto-published to GitHub pages using settings listed in the steps above.

## Tests

To run the test suite, you can run:

```
npm run test
```
