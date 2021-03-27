[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Total Lines](https://img.shields.io/tokei/lines/github/good-lly/gh-pages-help-center?color=green)
![GitHub stars](https://img.shields.io/github/stars/good-lly/gh-pages-help-center?style=social)
![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)

# 💡 Minimalistic FAQ/Help Center hosted on GitHub Pages

This is a minimalistic responsive Help Center hosted on GitHub pages written in vanilla JS. It does not need the maintenance of any servers or databases and can be hosted entirely on ❤️ GitHub for free!

Includes a very few dependencies:

-   [Fuse.js](https://fusejs.io/) for better fuzzy search
-   [Showdown](https://github.com/showdownjs/showdown) to convert
    markdown to HTML
-   Beatiful font [Inter](https://github.com/rsms/inter)

Feel free to customize by visual identity of your preference .)
To update `<head>` of your Help Center is recommended to follow [HEAD - A list of everything that _could_ go in the head of your document ](https://github.com/joshbuchea/HEAD)

Inspired by [Githu Pages URL shortener](https://github.com/nelsontky/gh-pages-url-shortener/).

## 💪 Motivation

Well, I want to convince my teammates that 99 global problems are possible to solve via GIT (or GitHub in this case)

> "See, I told You! Github!"
>
> _-- Peter_

Also we wanted to launch some simple FAQ but the most 3rd party tools are just limiting and cost us $$$. So, why not?

## 👨‍🏫 Demo time

[Here is a living example](sentienhq.com/help/) which we use on our own project & this is [(self-)help demo](https://good-lly.github.io/gh-pages-help-center/) 🤔 of this project that might help you.

## ☕ Features

1. The main feature is using a "database" in the form of GitHub issues and can be entirely hosted on GitHub pages.

-   Thanks to that you don't need to hassle around with the team management and access control
-   Gives your editor the ability to create markdown(HTML)-rich issues, comment on them, etc ...

2. Fuzzy search thanks to fuse.js _(What is fuzzy search? Generally speaking, fuzzy searching (more formally known as approximate string matching) is the technique of finding strings that are approximately equal to a given pattern (rather than exactly))_
3. Very simple - dummy setup. Written in vanilla old JS to work on IE, etc ...
4. Responsive (simple css grid layout included)
5. [Look ma, the DARK MODE!!! 🌙](https://good-lly.github.io/gh-pages-help-center/index_dark.html)

Please note there maybe still a [few issues!](https://github.com/good-lly/gh-pages-help-center/issues/4) Also for a full-featured help center experience, I do recommend you implement some live chat option. QAs are not enough sometimes. It also brings value to you - when you talk to customers! [thanks-captain-obvious.gif]

## ⚙️ Easy setup

I have extracted all important variables inside `index.html` file. So all you have to edit to make it work is there.

1. Fork/copy/download the repo.

2. Set up your [GitHub pages](https://pages.github.com/)

3. Edit endpoint `var GITHUB_ISSUES_LINK` to your repo issues inside the `index.html`. For example

```javascript
var GITHUB_ISSUES_LINK =
    'https://api.github.com/repos/good-lly/gh-pages-help-center/issues';
```

⚠️ avoid adding `/` after the end of path!

4. Edit two more self-explanatory lines under the endpoint.

```javascript
var GITHUB_ACCEPTED_CREATORS = ['good-lly'];
var GITHUB_ACCEPTED_LABELS = ['approved'];
```

Replace `'good-lly'` with the list of your editors' team. The `approved` label is reserved to make only those issues visible for visitors. This is good feature when you have multiple team members and you want to avoid showing FAQ/Help before it's proof-read/valid/approved by your team.

5. Add new issue inside the GitHub. Add `approved` and `test` for example.

6. Now you can edit the simple HTML to something like

```html
<div class="col-4">
    <h3>This is test</h3>
    <div class="content-box" data-label="test" data-order="newest"></div>
</div>
```

You can use a typical 12 column grid. Each `content-box` should have `data-label` and `data-order`.
Inside `data-label` you can specify multiple labels which should render. The order can be the `newest` and `oldest` for now. To list all issues as well as all uncategorized you can use reserved label names:

```javascript
var UNCATEGORIZED_LABEL = 'restUncategorizedEntries';
var ALL_LABEL = 'allEntries';
```

For example

```html
<h3>All popular or Recent</h3>
<div class="content-box" data-label="allEntries" data-order="newest"></div>

<h3>Uncategorized</h3>
<div
    class="content-box"
    data-label="restUncategorizedEntries"
    data-order="oldest"
></div>
```

7. That's it! have fun! 🥳
