# git-repo_tuto_main_manifest
Tutorial to understand git-repo (Google) logic : manage gits dependencies and sub-gits

## Install
Open your terminal :

> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null

> brew install repo

> brew install gpg


## Create the xml manifest

This file link the wanted git repositories and add them to your project.

Add default.xml in the repository's root.
Configure default.xml : link to wanted respositories and set where to put them.
Put in the tag "revision" the full commit hash.

You can use the terminal to get the full commit hash

> git log

Push the default.xml.

## Link the xml manifest and synchroniser

Link the project with the wanted manifest (by default it's "default.xml")

> repo init -u GIT_HTTPS_LINK -m XML_FILE

Examples for the demo :

> repo init -u https://git.hins.fr/ksavaroche/repo_manifest_demo -m default.xml

> repo init -u https://git.hins.fr/ksavaroche/repo_manifest_demo -m fizzbuzz.xml

Synchronise the repositories inside the manifests :

> repo sync
