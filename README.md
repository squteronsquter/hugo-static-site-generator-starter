# Hugo - Static site generator written in Go lang

Hugo is available at the following address: <https://gohugo.io/>

## To install and run Hugo locally

<https://gohugo.io/getting-started/quick-start/>

On MacOS

```
brew install hugo

hugo version

cd ~/your/hugo/development/folder

hugo new site yourhugowebsitename

cd yourhugowebsitename

git init

git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke

echo theme = \"ananke\" >> config.toml

```

This is more than enough to start, but you can also tweak the *config.toml* file.

Add a new post eg. first-post

```
hugo new posts/my-first-post.md

hugo server -D

```

The above command will run a local server on port 1313

So visit <http://localhost:1313> to view your fir website front page and see the post

Before you publish the post change the flag *draft: true* to *draft: false* and build the static website

```
hugo -D

```

# How to deploy your hugo website to your vps for example.

Use rsync to sync your local *public* folder with the remote public folder of your vps webserver

In my case the remote example server IP is 100.10.100.10 the user is root and ssh is only permitted with authorized keys.

I made a bash script *deploy* to take care of this, put it in the root of the local development environment, 

```
#!/bin/sh
USER=root
HOST=100.10.100.10
DIR=/var/www/example.com/public    # public directory path on remote host

hugo && rsync -avz --delete ./public/ -e "ssh -i /path/user/.ssh/authorizedkey_name" $USER@$HOST:$DIR

exit 0
```
made it executable and ran *./deploy*

```
chmod +x deploy

./deploy

```

## How to use next generation image formats in Hugo

<https://martijnvanvreeden.nl/hugo-shortcode-to-serve-images-in-next-gen-formats/>

## Ananke theme repository

<https://github.com/theNewDynamic/gohugo-theme-ananke/tree/a3dc1ac327c2c8c97e44168db7006b7f3c375917>

# Ananke theme - Tachyons colors

<http://tachyons.io/docs/themes/skins/>

***Happy coding***







