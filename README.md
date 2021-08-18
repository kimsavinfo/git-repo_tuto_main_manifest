# git-repo_tuto_main_manifest
Tutorial to understand git-repo (Google) logic: manage gits dependencies and sub-gits

## Install git-repo

Open your terminal:

> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null

> brew install repo

> brew install gpg

## Create gits

Git that will emulate libraries:
* git-repo_tuto_fizz
* git-repo_tuto_buzz

Git that will emulate a project:
* git-repo_tuto_myProject

## Create the xml manifest

This reposity is where all manifests are gathered together. 
You can consider it like a library with prebuilt architectures: you can pick one and import it, mix them or create your own.

The xml manifest is the file that load the wanted git repositories and add them to your project where you want.

Add default.xml in this repository's root.
Configure default.xml : link to wanted respositories and set where to put them. In this case, the tools "Fizz" and "Buzz" are linked.
Put in the tag "revision" the full commit hash.

You can use the terminal to get the full commit hash

> git log

Push the default.xml when you are done.

## Link the xml manifest and synchroniser

Create a projet: https://github.com/kimsavinfo/git-repo_tuto_myProject.

Link the project with the wanted manifest (by default it's "default.xml") with :

> cd /.../git-repo_tuto/myProject

> repo init -u GIT_HTTPS_LINK -m XML_FILE

Examples for the demo :

> repo init -u https://github.com/kimsavinfo/git-repo_tuto_main_manifest -m default.xml

> repo init -u https://github.com/kimsavinfo/git-repo_tuto_main_manifest -m fizz.xml

=> A hidden directory should be added: ".repo"

Synchronise the repositories inside the manifests :

> repo sync
