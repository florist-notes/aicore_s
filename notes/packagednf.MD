# dnf for RHEL

DNF = "Dandified YUM."

```bash
    $ dnf install httpd
    $ dnf install httpd-manual -y (assume yes)
    $ dnf check-update (check for updates)
    $ dnf update packagename -y
    $ dnf list installed (list installed packages)

    $ dnf install dnf-plugins-core
    $ dnf download httpd

    $ dnf install file.rpm (install local .rpm files)
    $ dnf remove httpd
    $ dnf reinstall httpd -y

    $ dnf repolist
    $ dnf repolist all

    $ dnf config-manager --add-repo="https://mirror.aarnet.edu.au/pub/centos/7"
Adding repo from: https://mirror.aarnet.edu.au/pub/centos/7 (add new repository)
    $ dnf --enablerepo=disabled-repo install package-example (enable or disable a specific repository)
    $ dnf search php (search for packages in repository)
    $ dnf provides */iscsiadm (find which package provides someething)
    $ dnf provides /etc/httpd/conf/httpd.conf (which package provides that file)
    $ dnf info httpd (view package info)
    $ dnf history
    $ dnf history info 13
    $ dnf history undo 13 -y
    $ dnf history redo
    $ tail /var/log/dnf.log
    $ dnf clean all (clear cached info)
    $ dnf install httpd -y -q (hide all output and -v for verbose)

```