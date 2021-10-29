<img src="piko.svg" height="24px">

_Piko is a minimal toolkit for html writing._

Piko is not a frontend framework or fancy site generator. Instead, Piko is the smallest step up possible from writing html completely by hand.

You don't need Piko if your site has a single html page. But if your site has more than one page, keeping the ```head``` tag synchronized between all pages can become annoying and error prone. Piko lets you extract the ```head``` tag into a separate file that can be reused and included on any page.

Piko also has a fast static web server with browser reload, and a tool for copying github template repos.

## Requirements

- [Install Deno](https://deno.land/manual/getting_started/installation) v1.15.3 on your computer.

## Install Piko

```bash
$ deno install -A https://cdn.jsdelivr.net/gh/learnpoint/piko@0.9.29/piko.js
```

Verify the installation:

```bash
$ piko -v

piko 0.9.29
```

## Upgrade Piko

```bash
$ piko upgrade
```

If you encounter any problems during the upgrade, the easiest way out is to install Piko from scratch:

1. Make sure you have the required version of Deno installed (see **Requirements** above).
2. Delete the Piko binaries (one or two files, depending on operating system). The binaries are located here:
    - Windows: ```%USERPROFILE%\.deno\bin```
    - Mac: ```$HOME/.deno/bin```
3. Install Piko from scratch (see **Installation** above).

## Getting started

1. Create a new site:

    ```bash
    $ piko create new-site
    ```
2. Start the dev server:

    ```bash
    $ cd new-site
    $ piko dev
    ```

3. Verify that your site is running at ```http://127.0.0.1:3333```

4. Edit the file ```new-site/src/index.html``` and save. The dev server should rebuild your site and reload the browser.

5. Stop the dev server using ```Ctrl+C```.

6. When done, deploy the ```docs``` folder to a static web host.

## Understanding the Piko folder structure

```
new-site
 ├── docs
 |    ├── about.html
 |    └── index.html
 └── src
      ├── components
      |    ├── header.html
      |    └── footer.html
      ├── about.md
      └── index.html
```

- The **```docs```** folder contains your compiled site. This folder can be deployed to a static web host like Netlify or GitHub Pages. Don't edit the files in this folder. Let Piko manage its content.

- The **```src```** folder is where you do your html writing.

- The **```src/components```** folder contains components that can be included in pages.

## Understanding Piko components

Piko components are files with html markup. They can be included in pages.

Components are located in the ```src/components``` folder.

Include a component using html comment syntax:

```html
<!-- header.html -->

<h1>Welcome</h1>

<!-- footer.html -->
```

Pass props to a component using JavaScript object syntax:

```html
<!-- header.html, { title: "Welcome" } -->

<h1>Welcome</h1>

<!-- footer.html -->
```

Inside a component, render props with ```{{ prop }}``` syntax:

```html
<title>{{ title }}</title>
```

You can provide a default prop value with ```||``` syntax:

```html
<title>{{ title || Home }}</title>
```

## Using markdown

Pages can be written in markdown. You can include components in markdown pages:

```md
<!-- header.html, { title: "Welcome"} -->

# Welcome

<!-- footer.html -->
```

Note that components must be written in html. Markdown is only supported in pages.

## Static web server

Piko has a very fast static web server that can be used on its own. It's completely cache-less and has build-in browser reload.

You can start the server from any folder:

```bash
$ piko serve
```

## Copy github template repositories

Piko has a tool for copying github repos. It downloads the files from a repo to your local computer, excluding files like ```LICENSE```, ```CNAME```, ```README.md```, ```.gitignore```, etc. It doesn't download the ```.git``` database, just the files in the latest commited tree.

Here's how to copy the github repo ```learnpoint/draft``` into a new folder named ```gradebook-idea```:

```bash
$ piko copy learnpoint/draft gradebook-idea
```


## Contributing

Piko is written with our specific use cases at [Learnpoint](https://github.com/learnpoint) in mind. We will not accept pull requests or fix issues that we don't experience at Learnpoint. We've written Piko for fun and for our own use.

That said, feel free to [create your own fork](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/fork-a-repo), or use Piko in any way you wish! ❤️
