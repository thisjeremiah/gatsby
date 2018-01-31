---
title: How to contribute
---

## Filing an issue

If you want your issue to be resolved quickly, please include in your issue:

* Gatsby version, node.js version, OS version
* The contents of your `gatsby-config.js` and `package.json` as well as your
  `gatsby-node.js`, `gatsby-browser.js` `gatsby-ssr.js` files depending on
  changes you've made there.

## Contributing

We want contributing to Gatsby to be fun, enjoyable, and educational for anyone and everyone. Contributions go far beyond pull requests and commits; we are thrilled to receive a variety of other contributions including the following:

* Blogging, speaking about, or creating tutorials about one of Gatsby's many features. Mention @gatsbyjs on Twitter and/or email shannon [at] gatsbyjs [dot] com so we can give pointers and tips (if you want them :) and help you spread the word. Please add your blog posts and videos of talks to our [Awesome Gatsby](/docs/awesome-gatsby/) page.
* Submitting new documentation; titles in _italics_ on gatsbyjs.org are stubs and need contributions
* Tweeting about things you build with @gatsbyjs (make sure to @ mention us!)
* Submitting documentation updates, enhancements, designs, or bugfixes
* Submitting spelling or grammar fixes
* Adding unit or functional tests
* Triaging GitHub issues -- especially determining whether an issue still persists or is reproducible
* Searching for Gatsby on Discord or Spectrum and helping someone else who needs help
* Teaching others how to contribute to Gatsby's repo!

If you are worried or don't know where to start, you can always reach out to Shannon Soper(@shannonb_ux) on Twitter or simply submit an issue and a maintainer can help give you guidance!

Looking to speak about Gatsby? We'd love to review your talk abstract/CFP! You can email it to shannon [at] gatsbyjs [dot] com and we can give pointers or tips!!!

### Special Note on Issues

If an issue is affecting you, start at the top of this list and complete as many tasks on the list as you can:

1. If there is an issue, +1 the issue to indicate that it's affecting you
2. If there's an issue and you can add more detail, write a comment describing how the bug is affecting OR if you can, write up a work-around for the bug
3. If there's not an issue, write the most complete description of what's happening, preferably with link to a Gatsby site that reproduces the problem
4. Offer to help fix the bug (and it's totally expected that you ask for help; open-source maintainers want to help contributors)
5. Deliver a well-crafted, tested PR

### Creating your own plugins and loaders

If you create a loader or plugin, we would <3 for you to open source it, and put it on npm.

### Contributing to the repo

Gatsby uses a "monorepo" pattern to manage its many dependencies and relies on
lerna and yarn to configure the repository for active development.

You can install the latest version of Gatsby by following these steps:

* Clone the repo, navigate to its directory.
* ensure you have the latest version of yarn installed (>= 1.0.2)
  https://yarnpkg.com/en/docs/install
* Install dependencies using `yarn run bootstrap` in the root of the repo.

The usual contributing steps are:

* Fork the [official repository](https://github.com/gatsbyjs/gatsby).
* Clone your fork: git clone `git@github.com:<your-username>/gatsby.git`
* setup up repo and Install dependencies: `yarn run bootstrap`
* Make sure tests are passing for you: `yarn test`
* Create a topic branch: `git checkout -b topics/new-feature-name`
* Run `npm run watch` from the root of the repo to first do an initial Babel
  build of all packages and then watch for changes to packages' source code and
  compile these changes on-the-fly as you work.
* Install [gatsby-dev-cli](/packages/gatsby-dev-cli/) globally: `yarn global add gatsby-dev-cli`
* Run `yarn install` in each of the sites you're testing with.
* For each of your Gatsby test sites, run the `gatsby-dev` command there to copy
  the built files from your cloned copy of Gatsby. It'll watch for your changes
  to Gatsby packages and copy them into the site. For more detailed instructions
  see the [gatsby-dev-cli README](/packages/gatsby-dev-cli/)
* Add tests and code for your changes.
* Once you're done, make sure all tests still pass: `yarn test`
* Commit and push to your fork.
* Create an pull request from your branch.

### Contributing to the documentation.

Gatsby, unsurprisingly, uses Gatsby for its documentation website.

If you want to add/modify any Gatsby documentation, go to the
[docs folder on Github](https://github.com/gatsbyjs/gatsby/tree/master/docs) and
use the file editor to edit and then preview your changes. Github then allows
you to commit the change and raise a PR right in the UI. This is the _easiest_
way you can contribute to the project!

However, if you want to make more changes to the website, that is, change
layouts, add sections/pages, follow the steps below. You can then spin up your
own instance of the Gatsby website and make/preview your changes before raising
a pull request.

* Clone the repo and navigate to `/www`
* Run `yarn` to install all of the website's dependencies.
* Run `gatsby develop` to preview the website in `http://localhost:8000`
* The Markdown files for the documentation live in `/docs` folder. Make
  additions or modifications here.
* Make sure to double check your grammar and capitalise correctly.
* Commit and push to your fork.
* Create a pull request from your branch.

## Development tools

### Redux devtools

Gatsby uses Redux for managing state during development and building. It's often
helpful to see the flow of actions and builtup state for a site you're working
on or if adding new functionality to core. We leverage
https://github.com/zalmoxisus/remote-redux-devtools and
https://github.com/zalmoxisus/remotedev-server to give you use the Redux
devtools extension for debugging Gatsby.

To use this, first install
[redux-devtools-extension](https://github.com/zalmoxisus/redux-devtools-extension)
in your browser. Then in your Gatsby repo, run `npm run remotedev`. Then in your
site directory run `REDUX_DEVTOOLS=true gatsby develop`. Depending on your
operating system and shell, you may need to modify how you set the
`REDUX_DEVTOOLS` environment variable.

At this point, your site will be sending Redux actions and state to the remote
server.

To connect to this, you need to setup the devtools extension to talk to the
remote server.

First open the remote devtools.

![how to open the redux remote devtools extension](./images/open-remote-dev-tools.png)

Then click settings along the bottom menu and set the host and port.

![how to set the host/port for the remote devtools extension to connect to Gatsby](./images/remote-dev-settings.png)

After this, the devtools extension _should_ connect to the remote server and
you'll see actions start showing up.

![gatsby redux remote devtools](./images/running-redux-devtools.png)

**Warning!! Lots of buginess**. While having this available is extremely
helpful, this setup is very buggy and fragile. There is a memory leak in the
extension that's triggered it seems every time you restart the Gatsby
development server. Also the extension often, for no apparent reason, just won't
show any actions from the remote server. It'll also often freeze up. The best
solution seems to just be turning everything off and on again. Fixing up these
tools would be very helpful for us and many others using these tools if someone
wants to take this on!
