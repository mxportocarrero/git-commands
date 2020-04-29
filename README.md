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
     IdentityFile ~/.ssh/<example_ssh_key1>

    # User2 Account Identity
     Host <user_2.gitlab.com>
     Hostname gitlab.com
     User mxportocarrero@gmail.com
     PreferredAuthentications publickey
     IdentityFile ~/.ssh/<example_ssh_key2>

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
    git push <remote_repo> <remote-branch>
    git push origin master
