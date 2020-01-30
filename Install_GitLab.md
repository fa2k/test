# GitLab

We use Omnibus Gitlab, CentOS7 yum package.

## GitLab overview

The gitlab server is at http://gitlab.nscamg.local

TODO: User accounts

Projects used in GitLab:

TODO Table


## Installation and configuration

The package is installed using

    # yum install gitlab-ee

Post-installation configuration including firewall rules:

    # firewall-cmd --permanent --add-service=http
    # firewall-cmd --permanent --add-service=https
    # reboot # or reload firewall

Edit `http://gitlab.nscamg.local`, the line with ``external_url``

    external_url 'http://gitlab.nscamg.local'

Then run

    # gitlab-ctl reconfigure

The interface is then available at http://gitlab.nscamg.local. It allows creation of the root user and setting a password.

After this, the gitlab can be used.

### SSH connection issue

In our case, accessing git repos over SSH didn't work. To fix SELinux permissions on ``/var/opt/gitlab/``, we repeated the configuration command:

    # gitlab-ctl reconfigure
