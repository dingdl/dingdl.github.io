# Building my personal website

Use [hugo](https://gohugo.io/) to build my personal website: https://dingdl.github.io/dingluo/.

## How to update the content in a Windows OS.

### Have Hugo on the computer in a minimal way. 
Download `hugo_xxxxx_Windows-64bit.zip` from [hugo releases](https://github.com/gohugoio/hugo/releases). Unzip the file and put the `hugo.exe` file in the root folder. To check the version of Hugo, enter the folder in terminal (e.g., powershell) and run `.\hugo.exe version`. You should be able to see something like `Hugo Static Site Generator v0.74.2-48565DE6 windows/amd64 BuildDate: 2020-07-17T17:22:50Z`.

### Update content and rebuild.
Once completing the update of content, run `.\hugo.exe -D`. All the website files will be generated in the folder of `public`. Now we need to rename this folder to `docs` before making a git commit. This is because GitHub Pages can only recognize website files in two ways: (1) Either all the files are in the root folder of the master brance; or (2) all the files are in the `docs` folder and in the repo settings we select `master branch/docs folder`. **Note for the option (2), it is only possible for the repo of which name is not `<your git handle>.github.io`.** That is why I rename this repo to `dingluo`, and the URL of the website is https://dingdl.github.io/dingluo/. 
