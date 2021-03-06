---
title: "Communicating Results Using Narratives"
---

Narratives are a method of data-driven storytelling.
They allow scientists (or anyone!) to author content which is displayed alongside the "normal" view of the data.
This content drives the way in which data is displayed, so instead of the user changing how things are displayed, the view automatically changes as you move between paragraphs in the narrative.
This allows you to communicate results with the appropriate views into the data, whilst maintaining the ability for the user to jump back to the "normal" viewing mode and interact with the data.


> Narratives are a new feature and there may still be bugs.
We're aiming to publicize this feature as soon as we have ensured everything's working as desired.


### How to Write a Narrative
A narrative is simply a [Markdown](https://en.wikipedia.org/wiki/Markdown) file with some quirks.
"Views" into the data are defined by specifying a Nextstrain URL in each paragraph's header which represents this view -- i.e. you can manipulate the app into the view you want and copy the resulting URL into the Markdown file.

#### YAML Frontmatter
This defines the author, title, and initial dataset.
It must appear at the top of the narrative file and looks like:

```yaml
---
title: "The current seasonal influenza A/H3N2 situation"
authors: "James Hadfield"
authorLinks: "https://twitter.com/hamesjadfield"
affiliations: "Fred Hutch, Seattle, USA"
date: "January 2018"
updated: "August 2018"
dataset: "https://nextstrain.org/local/flu/seasonal/h3n2/ha/3y?d=tree&p=full&c=num_date"
abstract: "This text serves as the abstract. This is optional."
---
```
Note that all the fields are optional, except for dataset, title, and authors.

#### Paragraphs
Each paragraph must start with a heading consisting of a link.
This link defines the dataset and settings used to display the data associated with the paragraph's content.
For instance, this paragraph displays the influenza A/H3N2 dataset, displaying only the phylogenetic tree and frequency panels, colored by region, and highlighting sequences collected since 2017. (The URL was obtained by manipulating the [nextstrain.org/flu](https://www.nextstrain.org/flu) page into the desired configuration).

```markdown
# [The situation since 2017](https://nextstrain.org/flu/seasonal/h3n2/ha/3y?c=region&d=tree,frequencies&dmin=2017-01-01&p=full)

These data show...
```

> Note that currently, the dataset can't change between paragraphs and that paragraphs which are too long are cut off (see "Known Bugs / Limitations" below).


### How to Share Narratives
Similar to [how community datasets are sourced from GitHub](/docs/contributing/community-builds) and accessible through nextstrain.org/community/..., so are narratives.
Given a repository at **github.com/orgName/repoName**, if there is a folder named **narratives** with the Markdown file **repoName.md**, then that dataset can be accessed via **nextstrain.org/community/narratives/orgName/repoName**.
Additional narratives named such as **repoName\_a\_b\_c.md** are available at **nextstrain.org/community/narratives/orgName/repoName/a/b/c**.


Our own narratives, which are stored in [this GitHub repo](https://github.com/nextstrain/narratives) are available to view at [nextstrain.org/narratives](https://www.nextstrain.org/narratives).
We're currently working at adding content and tutorials to these!

### Known Bugs / Limitations
* Datasets cannot be changed between paragraphs (i.e. the initial dataset is used for all subsequent paragraphs).
This will be fixed eventually.
* Text which is larger than the sidebar / page height is cut off.
This should be fixed soon.
* Styling may be slightly off on different browsers.
* Not all state is mirrored in the URLs (for instance, map bounds are not set in the URL).
This limits what views can be defined by paragraphs in the narratives.
* The frontmatter parsing will be extended to allow arrays of authors (etc).
