# The problem

Many build systems output static HTML, JavaScript and CSS to the `/dist` directory of the project.
To serve `/dist` on GitHub Pages and not have `/dist` appear in the URL path, `git subtree` or other tricks must be used.

* "[Deploying a subfolder to GitHub Pages](https://gist.github.com/cobyism/4730490)" - that gist has 370+ stars
* [gulp-gh-pages](https://www.npmjs.com/package/gulp-gh-pages) - 20,000 downloads/month
* [Yeoman needs to install git-subtree](https://github.com/yeoman/generator-gulp-webapp/blob/master/docs/recipes/gh-pages.md) and add yet nother gulp task

Symlinking `index.html` to `/dist/index.html` doesn't work - you can try this at http://dandv.github.io/gh-pages-symlink-fail.
But even if it did, other resources would need symlinking too, or `/dist/` paths in `index.html`, which is ugly.

Deploying the `/dist/` directory to gh-pages would be so much easier if GitHub Pages supported a setting to indicate the root directory to serve. You'd simply set it to `/dist`, make `gh-pages` your master branch, and be done with it.

# Dear GitHub Pages, please allow specifying the root folder

Then our workflow for deploying `/dist` to GitHub Pages wouldn't require any extra commands.

To set up a repo:

1. Create repo on GitHub and set the GitHub Pages directory to `/`
2. `git clone` it
3. `git checkout -b gh-pages`
4. `mkdir dist`
5. Edit files / build
6. `git add ... && git commit`
7. `git push origin gh-pages`
