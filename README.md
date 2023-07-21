# My website

Use [hugo](https://gohugo.io/) to build my website: https://dingdl.github.io.

## How to update deployment?
The webpage is hosted through [GitHub Pages](https://pages.github.com/). Currently no 
personal domain is used. If a domain needs to be used, the `baseURL` in `config.toml` 
has to be first modified and the hugo files need to be updated before being pushed to
the remote repo.

Current setting:
```
baseURL = "https://dingdl.github.io"
```

To update the deployment, the following step of compiling all 
the hugo files is needed.
```
hugo -D -d docs
```
`-d docs` makes all the website files go into the folder `docs`.  

Then push all the changes straight to the remote `master` branch.
```
git add .
git commit -m "Update content"
git push origin master
```

## Run local development server
```
hugo server
```
Then visit `http://localhost:1313` to check out the website.

## Change syntax highlighting
This hugo template uses [prism](https://prismjs.com/) to manage the syntax highlighting, which means we cannot make changes by using the following lines from the `config.toml`.
```
# Enable for syntax highlighting
PygmentsUseClasses = true
PygmentsCodeFences = true
PygmentsStyle = "monokai"
```
Instead, we need to download the `prism.js` and `prism.css` files of our selected theme and replace the ones in the current folder.
#### override the existing `prism.js` located in 
```
/themes/hello-friend-ng/assets/js/
```
#### override the existing `_prism.css` located in 
```
/themes/hello-friend-ng/assets/scss/
```

## On Windows
Download `hugo_xxxxx_Windows-64bit.zip` from [hugo releases](https://github.com/gohugoio/hugo/releases). Unzip the file and put the `hugo.exe` file in the root folder. To check the version of Hugo, enter the folder in terminal (e.g., powershell) and run `.\hugo.exe version`. You should be able to see something like `Hugo Static Site Generator v0.74.2-48565DE6 windows/amd64 BuildDate: 2020-07-17T17:22:50Z`.
