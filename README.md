# Github Hendrix Experience

Have you experienced problems with the GitHub Platform, since Microsoft acquisition ? 

I have been taking very seriously the Business event of Microsoft acquiring Github platform, last year (2018).

I am sure I am not the only engineer on that planet who did.

I have immediately (2018) begun working on something I have not released yet.

Today, April 29, 2019, I have experienced the most bizarre technical anomaly. I therefore decided to create this repo, to open discussion on the subject, with a technical first approach : 

* I propose you to add a new issue on that repo, to reference any problem you experienced while using Github
* I will reference here, all the issues I personally have experienced, which i'll call Hendrix' List : because if it takes me to use my teeth and tongue, to play the guitar, you bet I will.

## Hendrix' List

###  April 29, 2019 : the most bizarre SSH authentication technical anomaly

_Context_ 

I am working with multiple repos. I am building a software factory, so I just use SSH auth and private / public asymmetric key pairs.

Basically, this means that I do git clones using the following standard, worldwide-known mechanism : 

```sh
export GIT_SSH_COMMAND='ssh -i /path/to/my/private/key/on/any/machine/thats/mine/private_keyfile'

# 
# Most of the time, and very classicly : 
# [/path/to/my/private/key/on/any/machine/thats/mine/private_keyfile] is [~/.ssh/id_rsa]
# 

export EXAMPLE_GIT_REPO_SSH_URI=git@github.com:Jean-Baptiste-Lasselle/github_hendrix_experience.git

# 
# Yet, to wage a perfectly silent git clone we have authenticate to gihub using the SSH protocol : 
# To carry out such an authentication, we need to provide an id (username), in other words say who we claim  
# to be, along with the secret that will certify our bourne identity (the secret being the secret key)
# 

export THE_BOURNE_IDENTITY=Jean-Baptiste-Lasselle
git config --global user.name "$THE_BOURNE_IDENTITY"

# 
# That's all the infos we need to carry a git clone out, authenticating with the SSH protocol.
# 
# Note that you will find many examples on the web, where people also execute something like : 
# 
#     git config --global user.mail "bobby.ewing@dallas.io"
# 
# Specifying an email for Mister BOURNE, has nothing to do with the Bourne's identity, people 
# do that for a completely different purpose, or do that msitaking about its purpose.
# 


mkdir ./somewhere/beyond/the/sea
git clone $EXAMPLE_GIT_REPO_SSH_URI  ./somewhere/beyond/the/sea

# 
# which will silently clone repo to the [./somewhere/beyond/the/sea] folder
# 

```

Alright, if you now experience that yourself, using one of your repos, and one your Bourne's identities, well it won't work.

Unless you do one additional thing : In your Github's user settings menu, you'll have to add your PUBLIC key (the public key associated with your private key), to your user's public keys list. 
see Gthub's well documented Help section about that : https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account


_Anomaly_

So, doing that kind of git clones, here is what I today got : 

![obvious problem on github platform]()


