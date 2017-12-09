# counsel-tramp

Tramp ivy interface for ssh server and docker and vagrant

## Screencast

![counsel-tramp-gif](image/screencast.gif)

    M-x counsel-tramp

![counsel-tramp1](image/image1.png)

Display server list from your ~/.ssh/config with counsel interface.

![counsel-tramp2](image/image2.png)

Filter by counsel.

![counsel-tramp3](image/image3.png)

You can connect your server with tramp.

![counsel-tramp4](image/image4.png)

Selecting the list with sudo will lead to the server as root.

![counsel-tramp5](image/image5.png)

Selecting the list of '/sudo:root@localhost:/' will open file at localhost as root.

![counsel-tramp6](image/image6.png)

You can edit your server's nginx.conf on your emacs!

![docker-tramp](image/docker-tramp.png)

If you are using [docker-tramp](https://github.com/emacs-pe/docker-tramp.el), docker is also supplemented

If you are using [vagrant-tramp](https://github.com/dougm/vagrant-tramp), vagrant is also supplemented

![docker-tramp1](image/docker-tramp1.png)

You can edit docker container on your emacs!

![counsel-exit](image/exit.png)

When you finish editing nginx.conf you clean the tramp buffer with `tramp-cleanup-all-buffers` command.

Since I can not remember `tramp-cleanup-all-buffers` command I set a defalias called `exit-tramp`.

## Requirements

- Emacs 24.3 or higher
- counsel 0.10.0 or higher

## Installation

You can install `counsel-tramp.el` from [MELPA](http://melpa.org) with package.el
(`M-x package-install counsel-tramp`).

You can install `docker-tramp.el` from [MELPA](http://melpa.org) with package.el
(`M-x package-install docker-tramp`).

You can install `vagrant-tramp.el` from [MELPA](http://melpa.org) with package.el
(`M-x package-install vagrant-tramp`).

## Sample Configuration

	(setq tramp-default-method "ssh")
    (defalias 'exit-tramp 'tramp-cleanup-all-buffers)
    (define-key global-map (kbd "C-c s") 'counsel-tramp)

If the shell of the server is zsh it is recommended to connect with bash.

    (eval-after-load 'tramp '(setenv "SHELL" "/bin/bash"))

If you want to specify the user name to connect with docker-tramp.

	(setq counsel-tramp-docker-user "username")

If you want to specify multiple user name list to connect with docker-tramp.

	(setq counsel-tramp-docker-user '("username1" "username2" "username3" "username4"))

If you want to change initial directory when connecting with /sudo:root@localhost:.

	(setq counsel-tramp-localhost-directory "/var")

[melpa-link]: http://melpa.org/#/counsel-tramp
[melpa-badge]: http://melpa.org/packages/counsel-tramp-badge.svg
[melpa-stable-link]: http://stable.melpa.org/#/counsel-tramp
[melpa-stable-badge]: http://stable.melpa.org/packages/counsel-tramp-badge.svg
