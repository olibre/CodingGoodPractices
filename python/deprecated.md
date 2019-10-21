Configure
---------

Create file `~/.pip/pip.conf`

    [global]
    index-url = http://your.company.internal.hostname/jenkins/dev/+simple/
    trusted-host = your.company.internal.hostname
    
    [search]
    index = http://your.company.internal.hostname/jenkins/dev/
    trusted-host = your.company.internal.hostname


Install
-------

    sudo yum install python
    sudo yum install pip      # In order to download python packages


Download python packages
------------------------

Install dependencies of your project

    sudo -EH pip install watchdog
    sudo find /path/to/python/libs -type d -exec chmod -v a+rx {} '+' -o -exec  chmod -v a+r {} '+'

Some packages need other dependencies

    sudo yum install libyaml-devel gcc

Upgrade all `pip` packages

    sudo -EH /opt/exchange/Python/bin/pip list |
    while read package version
    do
        sudo -EH /opt/exchange/Python/bin/pip install --upgrade "$package"
    done
    sudo find /path/to/python/libs -type d -exec chmod -v a+rx {} '+' -o -exec  chmod -v a+r {} '+'
