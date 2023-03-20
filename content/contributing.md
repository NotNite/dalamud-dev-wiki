+++
title = "Contributing"
description = "Adding and editing pages on the wiki"
+++

This wiki is hosted [on GitHub](https://github.com/NotNite/dalamud-dev-wiki). If you want to add or edit a page, you can do so by creating a pull request.

## Frontmatter

Each page should have frontmatter at the top, like this:

```md
+++
title = "My cool page"
description = "This is a cool page"
+++
```

Do _not_ add first level headers (`#`), as they will be added from the `title` key.

## Linting & formatting

The wiki uses [Prettier](https://prettier.io/) and [markdownlint](https://github.com/DavidAnson/markdownlint). Lints will be checked via a GitHub Action.

To format with the Prettier CLI, run `prettier --write .`. To lint with the markdownlint CLI, run `markdownlint2 content/**/*.md`.

## Previewing

This wiki is written using Zola, so you can view it in your browser by running `zola serve`.

## Editing the navigation

While the table of contents is generated automatically, new files must be added to `nav.toml`. The `path` keyword should be the path to the file, without the `.md` extension, and without the `content/` prefix.

Entries should look like this:

```toml
[[nav]]
path = "contributing"
```

When you have children, you can add them like this:

```toml
[[nav]]
path = "test"
has_children = true

[[nav.children]]
path = "test/child"
```
