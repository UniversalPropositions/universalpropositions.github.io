---
title: "Universal Proposition Banks"
keywords: sample homepage
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: index.html
summary: This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages.
hide_sidebar: true
---

![UP: logo](https://universalpropositions.github.io/images/Universal_PropBank_Rev3.png) 

# Release

These is release 2.0 of the Universal Proposition Banks (UP). It is built upon [release 2.9 of the Universal Dependency Treebanks](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-4611) and inherits their [licence](https://lindat.mff.cuni.cz/repository/xmlui/page/licence-UD-2.9). We use the frame and role labels from the [English Proposition Bank](http://propbank.github.io/) version [3.0](https://github.com/propbank/propbank-documentation/blob/master/other-documentation/Description-of-PB3-changes.md).


**News (2022/01/01)**: Freezing UP1.0 ! 

**News (2019/10/01)**: Two domain-specific Propbank released ([Contract](https://developer.ibm.com/exchanges/data/all/contracts-proposition-bank/), [Finance](https://developer.ibm.com/exchanges/data/all/finance-proposition-bank/))! 

**News (2017/02/10)**: Initial version of Italian UP released!

**News (2017/01/31)**: Initial versions of Finnish, Portuguese and Spanish UP released!


## Multilingual SRL 

Using this data, we can create SRL systems that predict English PropBank labels for many different languages. See a recent demo screencast of this SRL for English, French and German [**here**](https://vimeo.com/161718580). 


## Introduction

This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages. 

For instance, consider the German sentence "Seine Arbeit wird von ehrenamtlichen Helfern und Regionalgruppen des Vereins unterstützt" (_His work is supported by volunteers and regional groupings of the association_). In CoNLL format, it looks like this, with English PropBank labels in the last two columns:

| Id | Form | POS | HeadId | Deprel | Frame | Role |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Seine | DET | 2 | det:poss | _ | _ |
| 2 | Arbeit | NOUN | 11 | nsubjpass | _ | **A1** |
| 3 | wird | AUX | 11 | auxpass | _ | _ |
| 4 | von | ADP | 6 | case | _ | _ |
| 5 | ehrenamtlichen | ADJ | 6 | amod | _ | _ |
| 6 | Helfern | NOUN | 11 | nmod | _ | **A0** |
| 7 | und | CONJ | 6 | cc | _ | _ |
| 8 | Regionalgruppen | NOUN | 6 | conj | _ | _ |
| 9 | des | DET | 10 | det | _ | _ |
| 10 | Vereins | NOUN | 8 | nmod | _ | _ |
| 11 | unterstützt | VERB | 0 | root | **[support.01](http://verbs.colorado.edu/propbank/framesets-english/support-v.html)** | _ |
| 12 | . | PUNCT | 11 | punct | _ | _ |

The German verb 'unterstützt' is labeled as evoking the '**support.01**' frame with two roles: "Seine Arbeit" (_his work_) is labeled **A1** (project being supported) and "ehrenamtlichen Helfern und Regionalgruppen des Vereins" (_volunteers and regional groupings of the association_) is labeled **A0** (the helper). 


### Format 

The universal propbank (UP) for each language consists of three files (training, dev and test data) with the extension `.conllu` but currently encoding an extension of the [CoNLL-U format](http://universaldependencies.org/format.html). The extension is based on the CoNLL format produced by the [Propbank conversion scripts](https://github.com/propbank/propbank-release/blob/master/docs/conll-conversion-notes.md), called `.gold_conll`. 

Besides the original 10 columns from the CoNLL-U format, the roleset column (column 11) gives the actual sense used, and that sense provides roleset specific meanings for each of the numbered arguments. Every column after the eleventh is a predicate, in order that they appear in the sentence. Note that the Propbank `.gold_conll` files contain a "frame file" column (column 11) that lets you know which ".xml" [file](https://github.com/propbank/propbank-frames/) contains the actual semantic form for the predicate in question (which is not always the same as the predicate: one must reference "lighten.xml" for lighten_up.02), but since all predicate identifier is unique, we haven't preserved this column.

The English dataset was the only one obtained in a different maner. See the README.org file in that directory for information.

In addition, each language has a folder with verb overview files (produced from the frame files) in html format. These files can be viewed in a browser and give an overview of all English frames that each target language verb can evoke.

### Scope

Our current focus is to annotate all target language verbs with appropriate English frames. This means that the scope of frame-evoking elements is currently limited to verbs. We also do not label target language auxiliary verbs. For each universal propbank, about 90% of all verbs are currently labeled. Unlabeled verbs often convey semantics for which we either could not find an appropriate English verb, or are part of complex verb constructions which we currently do not handle. 

### A note on quality 

This is an ongoing research project in which we use a combination of data-driven methods and some post-processing to generate these resources. This means that the labels in the UPs are mostly predicted over models trained on a different domain, which affects the quality. A good example is the German verb "angeben" which in our source data was mostly used in the "brag.01" sense, but in the German UD data is mostly used in the "report.01" sense, but almost never detected as such.

## Current and future work

This is an ongoing project which we are improving along three lines: (1) We are working on adding new languages to the current release. (2) We are working to curate the data to improve the quality of SRL annotation. (3) We are looking into extending the scope of frame-evoking-elements to other types of predicates besides verbs. (4) We will migrate the data to newer UD standard. 


## Publications

[Learning Explainable Linguistic Expressions with Neural Inductive Logic Programming for Sentence Classification](https://www.aclweb.org/anthology/2020.emnlp-main.345/). Prithviraj Sen, Marina Danilevsky, Yunyao Li, Siddhartha Brahma, Matthias Boehm, Laura Chiticariu and Rajasekar Krishnamurthy. *2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)* EMNLP 2020.

[A Novel Workflow for Accurately and Efficiently Crowdsourcing Predicate Senses and Argument Labels](https://www.aclweb.org/anthology/2020.findings-emnlp.38/). Youxuan Jiang, Huaiyu Zhu, Jonathan K. Kummerfeld, Yunyao Li and Walter Lasecki. *2020 Conference on Empirical Methods in Natural Language Processing: Findings (EMNLP)* EMNLP: Findings 2020.

[CLAR: A Cross-Lingual Argument Regularizer for Semantic Role Labeling](https://www.aclweb.org/anthology/2020.findings-emnlp.279/). Ishan Jindal, Yunyao Li, Siddhartha Brahma and Huaiyu Zhu. *2020 Conference on Empirical Methods in Natural Language Processing: Findings (EMNLP)* EMNLP: Findings 2020.

[Learning Explainable Linguistic Expressions with Neural Inductive Logic Programming for Sentence Classification](https://www.aclweb.org/anthology/P19-3023/). Prithviraj Sen, Yunyao Li, Eser Kandogan, Yiwei Yang and Walter Lasecki. *2019 57th Annual Meeting of the Association for Computational Linguistics: System Demonstrations* ACL:System Demonstration 2019.

[Crowd-in-the-Loop: A Hybrid Approach for Annotating Semantic Roles](https://www.aclweb.org/anthology/D17-1205). Chenguang Wang, Alan Akbik, Laura Chiticariu, Yunyao Li, Fei Xia and Anbang Xu. *2017 Conference on Empirical Methods on Natural Language Processing* EMNLP 2017.

[Active Learning for Black-Box Semantic Role Labeling with Neural Factors](http://static.ijcai.org/proceedings-2017/0405.pdf). Chenguang Wang, Laura Chiticariu and Yunyao Li. *2017 International Joint Conference on Artificial Intelligence* IJCAI 2017.

[Multilingual Aliasing for Auto-Generating Proposition Banks](http://alanakbik.github.io/papers/COLING_2016_aliasing.pdf). Alan Akbik, Xinyu Guan and Yunyao Li. *26th International Conference on Computational Linguistics* COLING 2016.

[K-SRL: Instance-based Learning for Semantic Role Labeling](http://alanakbik.github.io/papers/K_SRL.pdf). Alan Akbik and Yunyao Li. *26th International Conference on Computational Linguistics* COLING 2016.

[Multilingual Information Extraction with PolyglotIE](http://alanakbik.github.io/papers/coling2016-demo.pdf). Alan Akbik, Laura Chiticariu, Marina Danilevsky, Yonas Kbrom, Yunyao Li and Huaiyu Zhu. *26th International Conference on Computational Linguistics* COLING 2016.

[Towards Semi-Automatic Generation of Proposition Banks for Low-Resource Languages](http://alanakbik.github.io/papers/EMNLP-final.pdf). Alan Akbik, Vishwajeet Kumar and Yunyao Li. *2016 Conference on Empirical Methods on Natural Language Processing* EMNLP 2016.

[Polyglot: Multilingual Semantic Role Labeling with Unified Labels](http://alanakbik.github.io/papers/acl2016-demo.pdf). Alan Akbik and Yunyao Li. *54th Annual Meeting of the Association for Computational Linguistics* ACL 2016.

[Generating High Quality Proposition Banks for Multilingual Semantic Role Labeling](http://alanakbik.github.io/papers/acl2015.pdf). Alan Akbik, Laura Chiticariu, Marina Danilevsky, Yunyao Li, Shivakumar Vaithyanathan and Huaiyu Zhu. *53rd Annual Meeting of the Association for Computational Linguistics* ACL 2015.

## Preprint
[Improved Semantic Role Labeling using Parameterized Neighborhood Memory Adaptation](https://arxiv.org/pdf/2011.14459.pdf). Ishan Jindal, Ranit Aharonov, Siddhartha Brahma, Huaiyu Zhu and Yunyao Li. *arXiv preprint arXiv:2011.14459*



## People


### Core Team

* [Ishan Jindal](https://researcher.watson.ibm.com/researcher/view.php?person=ibm-Ishan.Jindal), IBM Research - Almaden
* [Alexandre Rademaker](http://researcher.ibm.com/researcher/view.php?person=br-alexrad), IBM Research - Brazil
* Michał Ulewicz, Kyndryl - Poland
* [Alan Akbik](http://alanakbik.github.io/), Humboldt-Universität zu Berlin, Germany
* [Laura Chiticariu](http://researcher.watson.ibm.com/researcher/view.php?person=us-chiti), IBM Watson
* [Marina Danilevsky](http://researcher.watson.ibm.com/researcher/view.php?person=us-mdanile), IBM Research - Almaden
* [Huaiyu Zhu](http://researcher.watson.ibm.com/researcher/view.php?person=us-huaiyu), IBM Research - Almaden
* [Yunyao Li](http://yunyaoli.github.io/), Apple

### Contributors

* Xinyu Guan, Yale University
* Tomer Mahlin, IBM Systems Division, Israel
* Vishwajeet Kumar, IIT Bombay
* [Fei Xia](http://faculty.washington.edu/fxia), University of Washington
* Chenguang (Ray) Wang, Amazon






<!-- {% include note.html content="If you're cloning this theme, you're probably writing documentation of some kind. I have a blog on technical writing here called <a alt='technical writing blog' href='http://idratherbewriting.com'>I'd Rather Be Writing</a>. If you'd like to stay updated with the latest trends, best practices, and other methods for writing documentation, consider <a href='https://tinyletter.com/tomjoht'>subscribing</a>. I also have a site on <a href='http://idratherbewriting.com/learnapidoc'>writing API documentation</a>." %}

## Build the Theme

Follow these instructions to build the theme.

### 1. Download the theme

First, download or clone the theme from the [Github repo](https://github.com/tomjoht/documentation-theme-jekyll). Most likely you won't be pulling in updates once you start customizing the theme, so downloading the theme (instead of cloning it) probably makes the most sense. In Github, click the **Clone or download** button, and then click **Download ZIP**.

### 2. Install Jekyll

If you've never installed or run a Jekyll site locally on your computer, follow these instructions to install Jekyll:

* [Install Jekyll on Mac][mydoc_install_jekyll_on_mac]
* [Install Jekyll on Windows][mydoc_install_jekyll_on_windows]

### 3. Install Bundler

In case you haven't installed Bundler, install it:

```
gem install bundler
```

You'll want [Bundler](http://bundler.io/) to make sure all the Ruby gems needed work well with your project. Bundler sorts out dependencies and installs missing gems or matches up gems with the right versions based on gem dependencies.

### 4. Option 1: Build the Theme (*without* the github-pages gem) {#option1}

Use this option if you're not planning to publish your Jekyll site using [Github Pages](https://pages.github.com/).

Bundler's Gemfile specifies how project dependencies are managed. Although this project includes a Gemfile, this theme doesn't have any dependencies beyond core Jekyll. The Gemfile is used to list gems needed for publishing on Github Pages. **If you're not planning to have Github Pages build your Jekyll project, delete these two files from the theme's root directory:**

* Gemfile
* Gemfile.lock

If you've never run Jekyll on your computer (you can check with `jekyll --version`), you may need to install the jekyll gem:

```
gem install jekyll
```

Now run jekyll serve (first change directories (`cd`) to where you downloaded the project):

```
jekyll serve
```

### 4. Option 2: Build the Theme (*with* the github-pages gem) {#option2}

If you *are* in fact publishing on Github Pages, leave the Gemfile and Gemfile.lock files in the theme.The Gemfile tells Jekyll to use the github-pages gem. **However, note that you cannot use the normal `jekyll serve` command with this gem due to dependency conflicts between the latest version of Jekyll and Github Pages** (which are noted [briefly here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)).

You need Bundler to resolve these dependency conflicts. Use Bundler to install all the needed Ruby gems:

```
bundle update
```

Then *always* use this command to build Jekyll:

```
bundle exec jekyll serve
```

If you want to shorten this long command, you can put this code in a file such as jekyll.sh (on a Mac) and then simply type `. jekyll.sh` to build Jekyll.

## Running the site in Docker

You can also use Docker to directly build and run the site on your local machine. Just clone the repo and run the following from your working dir:
```
docker-compose build --no-cache && docker-compose up
```
The site should now be running at [http://localhost:4000/](http://localhost:4000/).

This is perhaps the easiest way to see how your site would actually look.

## Configure the sidebar

There are several products in this theme. Each product uses a different sidebar. This is the essence of what makes this theme unique -- different sidebars for different product documentation. The idea is that when users are reading documentation for a specific product, the sidebar navigation should be specific to that product. (You can read more of my thoughts on why multiple sidebars are important in this [blog post](http://idratherbewriting.com/2016/03/23/release-of-documentation-theme-for-jekyll-50/).)

The top navigation usually remains the same, because it allows users to navigate across products. But the sidebar navigation adapts to the product.

In each page's frontmatter, you must specify the sidebar you want that page to use. Here's an example of the page frontmatter showing the sidebar property:

<pre>
---
title: Alerts
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "You can insert notes, tips, warnings, and important alerts in your content. These notes are stored as shortcodes made available through the linksrefs.hmtl include."
<span class="red">sidebar: mydoc_sidebar</span>
permalink: mydoc_alerts
---
</pre>

The `sidebar: mydoc_sidebar` refers to the \_data/sidebars/mydoc_sidebar.yml file.

Note that your sidebar can only have 2 levels (expand the **Tag archives** option to see an example of the second level). Given that each product has its own sidebar, this depth should be sufficient (it's really like 3 levels). Deeper nesting goes against usability recommendations.

You can optionally turn off the sidebar on any page (e.g. landing pages). To turn off the sidebar for a page, you should set the page frontmatter tag as `hide_sidebar: true`.

If you don't declare a sidebar, the `home_sidebar` file gets used as the default because this is the default specified in the config file:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

If you want to set different sidebar defaults based on different folders for your pages, specify your defaults like this:

```
-
  scope:
    path: "pages/mydoc"
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: mydoc_sidebar
    topnav: topnav
```

This would load the `mydoc_sidebar` for each file in **pages/mydoc**. You could set different defaults for different path scopes.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation].

## Top navigation

The top navigation works just like the sidebar. You can specify which topnav data file should load by adding a `topnav` property in your page, like this:

```yaml
topnav: topnav
```

Here the topnav refers to the `_data/topnav.yml` file.

Because most topnav options will be the same, the `_config.yml` file specifies the topnav file as a default:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

## Sidebar syntax

The sidebar data file uses a specific YAML syntax that you must follow. Follow the sample pattern shown in the theme, specically looking at `mydoc_sidebar.yml` as an example: Here's a code sample showing all levels:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    - title: Get started
      url: /index.html
      output: web, pdf
      type: homepage

    - title: Introduction
      url: /mydoc_introduction.html
      output: web, pdf

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Tag archives
    output: web
    folderitems:

    - title: Tag archives overview
      url: /mydoc_tag_archives_overview.html
      output: web

      subfolders:
      - title: Tag archive pages
        output: web
        subfolderitems:

        - title: Formatting pages
          url: /tag_formatting.html
          output: web

        - title: Navigation pages
          url: /tag_navigation.html
          output: web

        - title: Content types pages
          url: /tag_content_types.html
          output: web
```

Each `folder` or `subfolder` must contain a `title` and `output` property. Each `folderitem` or `subfolderitem` must contain a `title`, `url`, and `output` property.

The two outputs available are `web` and `pdf`. (Even if you aren't publishing PDF, you still need to specify `output: web`).

The YAML syntax depends on exact spacing, so make sure you follow the pattern shown in the sample sidebars. See my [YAML tutorial](mydoc_yaml_tutorial) for more details about how YAML works.

{% include note.html content="If you have just one character of spacing off, Jekyll won't build due to the YAML syntax error. You'll see an error message in your console that says \"Error ... did not find expected key while parsing a block mapping at line 22 column 5. Error: Run jekyll build --trace for more information.\" If you encounter this, it usually refers to incorrect indentation or spacing in the YAML file. See the example mydoc_sidebar.yml file to see where your formatting went wrong." %}

Each level must have at least one topic before the next level starts. You can't have a second level that contains multiple third levels without having at least one standalone topic in the second level. If you need a hierarchy that has a folder that contains other folders and no loose topics, use a blank `-` item like this:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    -

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Installation
    output: web, pdf
    folderitems:

    - title: About Ruby, Gems, Bundler, etc.
      url: /mydoc_about_ruby_gems_etc.html
      output: web, pdf

    - title: Install Jekyll on Mac
      url: /mydoc_install_jekyll_on_mac.html
      output: web, pdf

    - title: Install Jekyll on Windows
      url: /mydoc_install_jekyll_on_windows.html
      output: web, pdf
```

To accommodate the title page and table of contents in PDF outputs, each product sidebar must list these pages before any other:

```yaml
- title:
  output: pdf
  type: frontmatter
  folderitems:
  - title:
    url: /titlepage
    output: pdf
    type: frontmatter
  - title:
    url: /tocpage
    output: pdf
    type: frontmatter
```

Leave the output as `output: pdf` for these frontmatter pages so that they don't appear in the web output.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation] and [YAML tutorial][mydoc_yaml_tutorial].

## Comments

The theme integrates [Commento.io](https://commento.io/) for comments below pages and posts. (This commenting service doesn't inject controversial tracking ads like Disqus does.) You will need to Commento.io account + plan ($5/month) to authorize Commento with your domain (no other configuration should be required). If you don't want comments, in the \_config.yml file, change the `comments: true` properties (under `defaults`) to `comments: false` in every instance. Then in the commento.html include file (inside \_includes), the `{% raw %}{% unless page.comments == false %} ... {% endunless %}{% endraw %}` logic will not insert the Commentio form.

## Relative links and offline viewing

This theme uses relative links throughout so that you can view the site offline and not worry about which server or directory you're hosting it. It's common with tech docs to push content to an internal server for review prior to pushing the content to an external server for publication. Because of the need for seamless transferrence from one host to another, the site has to use relative links.

To view pages locally on your machine (without the Jekyll preview server), they need to have the `.html` extension. The `permalink` property in the page's frontmatter (without surrounding slashes) is what pushes the files into the root directory when the site builds.

## Page frontmatter

When you write pages, include these same frontmatter properties with each page:

```yaml
---
title: "Some title"
tags: [sample1, sample2]
keywords: keyword1, keyword2, keyword3
last_updated: Month day, year
summary: "optional summary here"
sidebar: sidebarname
permalink: filename.html
---
```

(You will customize the values for each of these properties, of course.)

For titles, surrounding the title in quotes is optional, but if you have a colon in the title, you must surround the title with quotation marks. If you have a quotation mark inside the title, escape it first with a backlash `\`.

Values for `keywords` get populated into the metadata of the page for SEO.

Values for `tags` must be defined in your \_data/tags.yml list. You also need a corresponding tag file inside the tags folder pages/tags/ that follows the same pattern as the other tag files shown in the tags folder. (Jekyll won't auto-create these tag files.)

If you don't want the mini-TOC to show on a page (such as for the homepage or landing pages), add `toc: false` in the frontmatter.

The `permalink` value should be the same as your filename and include the ".html" file extension.

For more detail, see [Pages][mydoc_pages].

## Where to store your documentation topics

You can store your files for each product inside subfolders following the pattern shown in the theme. For example, product1, product2, etc, can be stored in their own subfolders inside the \_pages directory. Inside \_pages, you can store your topics inside sub-subfolders or sub-sub-folders to your heart's content. When Jekyll builds your site, it will pull the topics into the root directory and use the permalink for the URL.

Note that product1, product2, and mydoc are all just sample content to demonstrate how to add multiple products into the theme. You can freely delete that content.

For more information, see [Pages][mydoc_pages] and [Posts][mydoc_posts].

## Configure the top navigation

The top navigation bar's menu items are set through the \_data/topnav.yml file. Use the top navigation bar to provide links for navigating from one product to another, or to navigate to external resources.

For external URLs, use `external_url` in the item property, as shown in the example topnav.yml file. For internal links, use `url` the same was you do in the sidebar data files.

Note that the topnav has two sections: `topnav` and `topnav_dropdowns`. The topnav section contains single links, while the `topnav_dropdowns` section contains dropdown menus. The two sections are independent of each other.

## Generating PDF

If you want to generate PDF, you'll need a license for [Prince XML](http://www.princexml.com/). You will also need to [install Prince](http://www.princexml.com/doc/installing/).  You can generate PDFs by product (but not for every product on the site combined together into one massive PDF). Prince will work even without a license, but it will imprint a small Prince image on the first page, and you're supposed to buy the license to use it.

If you're on Windows, install [Git Bash client](https://git-for-windows.github.io/) rather than using the default Windows command prompt.

Open up the css/printstyles.css file and customize the email address (`youremail@domain.com`) that is listed there. This email address appears in the bottom left footer of the PDF output. You'll also need to create a PDF configuration file following the examples shown in the pdfconfigs folder, and also customize some build scripts following the same pattern shown in the root: pdf-product1.sh

See the section on [Generating PDFs][mydoc_generating_pdfs] for more details about setting the theme up for this output.

## Blogs / News

For blog posts, create your markdown files in the \_posts folder following the sample formats. Post file names always begin with the date (YYYY-MM-DD-title).

The news/news.html file displays the posts, and the news_archive.html file shows a yearly history of posts. In documentation, you might use the news to highlight product features outside of your documentation, or to provide release notes and other updates.

See [Posts][mydoc_posts] for more information.

## Markdown

This theme uses [kramdown markdown](http://kramdown.gettalong.org/). kramdown is similar to Github-flavored Markdown, except that when you have text that intercepts list items, the spacing of the intercepting text must align with the spacing of the first character after the space of a numbered list item. Basically, with your list item numbering, use two spaces after the dot in the number, like this:

```
1.  First item
2.  Second item
3.  Third item
```

When you want to insert paragraphs, notes, code snippets, or other matter in between the list items, use four spaces to indent. The four spaces will line up with the first letter of the list item (the <b>F</b>irst or <b>S</b>econd or <b>T</b>hird).

```
1.  First item

    ```
    alert("hello");
    ```

2.  Second item

    Some pig!

3.  Third item
```

See the topics under "Formatting" in the sidebar for more information.

## Automated links

If you want to use an automated system for managing links, see [Automated Links][mydoc_hyperlinks.html#automatedlinks]. This approach automatically creates a list of Markdown references to simplify linking.

## Other instructions

The content here is just a getting started guide only. For other details in working with the theme, see the various sections in the sidebar.

{% include links.html %}
 -->
