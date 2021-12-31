# React

## Deploying to GitHub Pages

```shell
npx create-react-app app-name
cd app-name
npm install gh-pages --save-dev
```

`package.json` file:

- At the top level, add a `homepage` property:

```js
//... same level with name and vesion
"homepage": "http://{username}.github.io/{repo-name}"
```

- add a `predeploy` property and a `deploy` property, each having the values shown below:

```js
"scripts": {
 //...
 "predeploy": "npm run build",
 "deploy": "gh-pages -d build"
}
```

```shell
git init
git remote add origin https://github.com/yxshi610/characters.git
npm run deploy    // accessible through URL
```

- optionally commit to "master" branch

```shell
git add .
git commit -m "Create a React app and publish it to GitHub Pages"
git push origin master
```

the `master` branch held the source code, and the `gh-pages` branch held the *built* app code.

Problem: GitHub Pages doesn't natively support single page apps. When there is a fresh page load for a url like `example.tld/foo`, where `/foo` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of `/foo`.

Solution: [GitHub - rafgraph/spa-github-pages: Host single page apps with GitHub Pages](https://github.com/rafgraph/spa-github-pages)

change to Surge:

```shell
npm run build
cd build
cp index.html 200.html
surge
```
