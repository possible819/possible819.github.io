https://possible819.github.io

## Find where theme sources are...

```bash
# bundle info --path $THEME_NAME
$ bundle info --path minima
/home/jaylee/gems/gems/minima-2.5.1
```

## Create post via `generator-jekyll-doc`

Refer: https://github.com/possible819/generator-jekyll-doc

```sh
# clone generator-jekyll-doc to local
git clone https://github.com/generator-jekyll-doc

# move into cloned project directory
cd ./generator-jekyll-doc

# install dependencies to run it
npm install

# make link to use it anywhere you want to
npm link

# change directory to where you want to create template file
cd ../git-page-repo

# install yo if it's not installed yet
npm install -g yo

# excuting generator to create posting template
yo jekyll-dock:post
```
