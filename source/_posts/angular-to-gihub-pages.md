---
title: Deploying an Angular App to Github Pages
date: 2019-11-24 20:26:11
tags:
---
> Github pages is a Github feature that allows you to host a static website or web app for free, and it’s as simple as putting the files in a gh-pages branch of your project’s repository. The Angular CLI, along with a node package called angular-cli-ghpages make it even easier to deploy to Github pages.

First install the angular-cli-ghpages globally:
```code
$ npm install -g angular-cli-ghpages
```
Now use the Angular CLI with the --base-href flag to build your project and set the correct base href loaction:
```code
$ ng build --prod --base-href "<repo-name>"
```
If the `--base-href` is not set then we can just use
```code
$ ng build --prod
```
Then it’s as simple as running angular-cli-ghpages. You can use the ngh shorthand:
```code
$ ngh
```
And done! Your app will now be hosted at https://username.github.io/app-name/

You can optionally add a message to the commit when deploying:
```code
$ ngh --message="First deploy"
```
You can also specify which branch to deploy:
```code
$ ngh --branch=production
```
And finally, you can always do a dry run before actually deploying to see the output:
```code
$ ngh --dry-run
```