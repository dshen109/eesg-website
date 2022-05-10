# Electric Energy Systems Group Website


## Local Build Instructions

Install hugo from the source binaries (especially on Ubuntu, since installing via `apt-get` will give you an older version).

Run

```bash
hugo server
```

## Website Update Instructions

To make an update to a section of the website, first make a new git branch. You
will not be able to push your changes directly to main. Once you have made
the changes, verify that your content is how you want it to appear by running
`hugo server` and browsing the new website on your local machine.

Finally, open a pull request in Github to merge your changes into the main
branch. The hosted website should automatically update after your changes
are merged and built.

You should only have to modify files in `content/` to make updates. For more
detailed documentation, see the
[Wowchemy documentation](https://wowchemy.com/docs/)

### Creating a news post

News posts reside in `content/post`. You can add a featured image by uploading
an image named `featured.jpg` to the post object's folder. For announcements
that already have external webpages, you can avoid duplicating ocntent with
the `external_link` key:

```yaml
---
title: Marija Ilic receives the IEEE PES Outstanding Power Engineering Educator award
date: 2020-08-04
image:
  focal_point: 'middle'
external_link: https://ieeetv.ieee.org/ieeetv-specials/ieee-pes-awards-2020-ieee-pes-outstanding-power-engineering-educator-award
profile: false
reading_time: false
---
```

For posts where you want to add text to the website itself, you can add it
using markdown after the yaml config:

```yaml
---
title: Marija Ilic delivers keynote talk at 2019 FREEDM Research Symposium
date: 2019-10-12
image:
  focal_point: 'middle'
---
Prof. Marija Ilic was invited to deliver a keynote speech at the Future
Renewable Electric Energy Delivery and Management
([FREEDM](https://www.freedm.ncsu.edu/)) Research Symposium.

<!--more-->
Her presentation titled ‘The Future of Electric Power Grid ‘ can be found [here](https://www.freedm.ncsu.edu/wp-content/uploads/2019/04/Ilic-MIT-Future-of-the-Grid.pdf).
```

### Creating a project

- Pick a project name. The name should be all lowercase and use hyphens instead
  of spaces. The name will be used to link other items
  (publications, presentations) to the project.
- Make a new folder `content/project/projectname` (do not make a folder in `content/projects`)
- copy the following template to a file titled `index.md` in the project folder:


```yaml
---

title: ProjectTitleHere
# the authors should correspond to folder names in content/authors
authors:
  - author1
  - author2
# add 'ongoing' if the project is ongoing
tags:
  - ongoing
  - tag2
# Date the project started (approximate)
date: 2019-11-20T12:52:43-04:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# URL for external lines
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
# Your project description goes here. The text will be displayed via markdown.

A few sentences describing what the project is.

**Funding Agency:** Project funder
```

### Adding a group member

First, make a folder `content/authors/name` to store the member's
information. The `name` folder should be the member's last name, all lowercase.
The name of this folder is used to cross-reference their profile with the
`author` field in projects and publications.

Then, add their image as `content/authors/name/avatar.jpg` (PNG format
is also fine).

Finally, create the file `content/authors/name/_index.md`, filling in the
following:

```yaml
---
# Display name
title: First, Last

# Is this the primary user of the site?
superuser: False

# Role/position
role: Graduate Student, Postdoctoral Associate, etc.

# Organizations/Affiliations
organizations:
  - name: MIT Department of Electrical Engineering & Computer Science
    url: ''

# Comment out any items that are not applicable for the user.
social:
  - icon: envelope
    icon_pack: fas
    link: 'mailto:mit-email@mit.edu'
  - icon: google-scholar
    icon_pack: ai
    link: google scholar link here
  - icon: github
    icon_pack: fab
    link: github link here
  - icon: linkedin
    icon_pack: fab
    link: linkedin link here

# Highlight the author in author lists? (true/false)
highlight_name: true

# Organizational groups this person belongs to.
user_groups:
  - Postdocs
  - Grad Students
  - Previous PhD Students
  - Previous Masters Students
---

Member bio goes here.

```


### Creating a publication
