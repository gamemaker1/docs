# Beckn Developer Documentation Proposal

This proposal outlines a plan to use Gatsby to render `.mdx` files pulled from a
single GitHub repository.

## Repository structure

The repository (`beckn/developer-docs`) will be organized as follows:

```
.
├── content/
│  ├── examples/
│  │  ├── 0.9.3/
│  │  └── 0.9.2/
│  ├── overview/
│  │  └── index.mdx
│  ├── projects/
│  │  ├── beckn-in-a-box/
│  │  └── transit-ticketing-system/
│  └── reference/
│     └── 0.9.3/
│        ├── core/
│        ├── infra/
│        ├── logistics/
│        ├── mobility/
│        └── retail/
├── source/
│  ├── components/
│  ├── templates/
│  ├── utils/
│  └── index.tsx
├── license.md
├── package.json
├── pnpm-lock.yaml
└── readme.md
```

The `content/` folder will contain all of the documentation as `.md` (Markdown)
or `.mdx` (Markdown + React) files. The `source/` folder will contain the source
code for the Gatsby website. We could use
[this](https://github.com/hasura/gatsby-gitbook-starter) starter template to get
started with Gatsby quickly.

## Website Structure

The website would be split into 4 sections:

- Overview
- Spec and API Reference
- Build with Beckn
- Projects

### Overview

This section will consist of an introduction to the Beckn protocol. It already
exists as https://developers.becknprotocol.io/docs/introduction/.

These pages will be placed in the `content/overview/` folder.

### Spec and API Reference

This section consists of the specification, API reference and schema definitions
for each version and each sector. It already exists at
https://developers.becknprotocol.io/docs/core-specification/.

These pages will be placed under the `content/reference/{version}/{sector}/`
folder.

### Build with Beckn

This section consists of code snippets to take on different problems using the
Beckn protocol in multiple programming languages. It already exists as
https://developers.becknprotocol.io/build-with-beckn/.

This section will have a different UI - with the capability to search through
them based on language, sector, APIs used, etc. All of these parameters will be
tags provided on the pages as frontmatter.

These pages will be placed under the `content/examples/{version}/` folder.

### Projects

This section will consist of projects that use the Beckn protocol. It already
exists as https://developers.becknprotocol.io/projects/.

This section will also have a different UI and show each project as a card on
the main page. Clicking on a card should take you to the overview of the
project.

These pages will be placed under the `content/projects/{name}/` folder.

## Creating and Updating Content

Each page will have an edit button at the top right (near the print button on
the current website). Clicking this button will bring up a Markdown editor which
can be used to edit the page.

Once the user has finished making changes, they can click a `Propose Changes`
button that will take them to `fork and propose changes` page on the
`beckn/developer-docs` repository. Note that this will need them to sign in with
their GitHub account. The user can then create a pull request on the
`beckn/developer-docs` repository.

A GitHub action (https://github.com/enriikke/gatsby-gh-pages-action) will
automatically re-deploy the Gatsby website on a push/merge to the `main` branch
with the changed content.

Creating content goes through the same process. However, the user will need to
enter the filename for the new page - and the new page can automatically be
placed in the right folder based on the section the user is in.

## Development

Any changes pushed to the `main` branch will be deployed to the main website
immediately. Hence, the `main` branch should be set as a `protected` branch on
GitHub, development should occur on the `develop` branch and merging onto the
`main` should only occur if the site builds and all tests pass.
