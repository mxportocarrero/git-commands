# git-commands
Various git commands for setting correctly SSH-Keys and other misteries in the git world

## Generaate SSH Keys
creates a new SSH key pair, using the provided email as a label. some command examples

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ssh-keygen -t ed25519 -C "<comment>" # Gitlab

## Multiple Accounts on a Single GitHub instance
you can dedfine host aliases inside ***~/.ssh/config*** file

    # User1 Account Identity
    Host <user_1.gitlab.com>
     Hostname gitlab.com
     User mxportocarrero@gmail.com
     PreferredAuthentications publickey
     AddKeysToAgent yes
     IdentityFile ~/.ssh/<example_ssh_key1>

    # User2 Account Identity
     Host <user_2.gitlab.com>
     Hostname gitlab.com
     User mxportocarrero@gmail.com
     PreferredAuthentications publickey
     AddKeysToAgent yes
     IdentityFile ~/.ssh/<example_ssh_key2>

Keys to Agent allow to passphrase to be remembered after one successful authentication. You may need to start and Authentication agent for this feature to work

    eval $(ssh-agent)

Setting host aliases allow us to have multiple remotes

    $ git remote add one account-one:repository.git
    $ git remote add two account-two:repository.git

and different push repositories

    $ git push one master
    $ git push two master

## Clonning repositories using custom hosts
    git clone git@<user_1.gitlab.com>:gitlab-org/gitlab.git

or, setting up a new remote repository

    git remote set-url origin git@<user_1.gitlab.com>:gitlab-org/gitlab.git

## Test Connection through SSH
-v option enables printing debug logs

    ssh -vT git@github.com
    ssh -vT git@<Host-Alias>

## Show remote repository info
    git remote show origin

## Pushing to remote repository
    git push <remote_repo> <branch>
    git push origin master

## Managing local and remote branches
tell Git server to track newly created local branch. that is, create remote branch from local

    git push -u origin dev

oe if you want to change or forgot setting a remote branch

    git branch -u origin/dev
