
# FORSYTE website

## Running locally
After installing `hugo`, you can run a server locally from the root of the repository:
```sh
hugo server -D
```

## Adding/modifying people
A new person can be added by running the following command:
```sh
hugo new people/<name>.md
```
One can alternatively create such files based on `archetypes/people.md`.

A person file can contain key-value pairs (see `archetypes/people.md`) that are automatically rendered on each person page
and custom content, under the markdown part of the file. This custom content can contain HTML code but note that it will
be added to predefined containers, so please check whether the content is rendered as expected.

People are assigned special values via the `roles` and `groups` keys in their markdown files.
A role is the person's job or other role within FORSYTE and the group is one of the research groups.
Note that any number of roles and groups can be assigned to a person (including 0) but it affects where
and how the person appears on the website. E.g. a person can appear in multiple groups and also as
other staff.

If a person graduates, their `alumni` flag should be assigned `true` to show them in the Alumni section.

## Adding news posts
A news post article be added with the following command:
```sh
hugo new news/<article>.md
```
Then, after modifying the title to the desired value, one can add custom HTML code under the markdown part of this file,
which will appear as the content of the news article.

## Adding bibliographic entries
One way to extend the bibliography with new citations is simply adding new entries to an
existing bibliography file under `content/publications`, e.g. `content/publications/0.md`.
Otherwise, using [pandoc](https://pandoc.org/) version [2.16.2](https://github.com/jgm/pandoc/releases/tag/2.16.2), running the following command on a BibTeX file:
```sh
pandoc <file> -s -f biblatex -t markdown -o <output>.md
```
Then, either copying the elements under the `references` key from this file to one of the
existing bibliography file works, or adding `<output>.md` to `content/publications` folder.