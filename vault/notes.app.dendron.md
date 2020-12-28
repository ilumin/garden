---
id: 4c98bf7a-7e61-4cf2-9f36-f3deed0c09ae
title: Dendron
desc: "A Hierarchical note taking extension for VSCode"
updated: 1609147275940
created: 1609124719874
---

# Dendron

## Setup

- open `vscode`
- install extension by search `dendron` ~ install everything 😍
- open command and run `>Dendron: Initialize workspace` and pick some favorite folder to use as Dendron's workspace
- start note taking !

## Setup "Digital Garden"

Dendron have 2 build-in website publisher "Jekyll" and "11ty"  
I've use "11ty", since I'm a fanboy of Node.js not Ruby.

- goto workspace folder
- run

  ```sh
  npm init -y
  npm i @dendronhq/dendron-cli@latest @dendronhq/dendron-11ty@latest
  ```

  that's it you'll have Dendron's cli and 11ty theme installed on workspace

- you may need to add some files to manage workspace  
   for me, I've added `.gitignore`, `.editorconfig` and update `package.json`

  **.gitignore**

  ```
  # node modules folder
  node_modules/
  # the build folder
  build/
  # the compiled notes
  docs/notes/
  ```

  **.editorconfig**

  ```
  root = true

  [*]
  end_of_line = lf
  insert_final_newline = true
  charset = utf-8
  indent_style = space
  indent_size = 2
  ```

  **package.json**

  ```
  ...
  "script": {
    "start": "dendron-cli buildSiteV2 --wsRoot . --stage dev --serve",
    "build": "dendron-cli buildSiteV2 --wsRoot . --stage prod"
  },
  ...
  ```

- run local digital garden `npm run start` then open `http://localhost:8000/`

## Publish to Github page

- edit Dendron's config in `{WORK_SPACE}/dendron.yml`

  **dendron.yml**

  ```yml
  version: 1
  vaults:
    - fsPath: vault
  site:
  copyAssets: true
  siteHierarchies:
    - books
    - notes
  siteRootDir: docs
  gh_edit_repository: "https://github.com/ilumin/notes"
  logo: "vault/assets/images/logo.svg"
  siteUrl: "https://ilumin.dev"
  siteProtocol: https
  title: "ilumin's Digital Garden"
  author: "ilumin"
  twitter: "ilumin"
  description: "ilumin don't remember and don't want to loose all memory, ilumin'll jot down and plant in this digital garden."
  usePrettyRefs: true

  githubCname: "ilumin.dev"
  gh_edit_link: false
  ```

## Read more

- [Dendron Publishing V2](https://dendron.so/notes/857936de-1bd5-4666-8ea9-a218d426c7ec.html)
- [Mixed content error when using github pages with custom domain](https://stackoverflow.com/questions/46672558/mixed-content-error-when-using-github-pages-with-custom-domain)
- [Managing a custom domain for your Github Pages site](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site)
- [Using custom domain for GitHub pages](https://medium.com/@hossainkhan/using-custom-domain-for-github-pages-86b303d3918a)
