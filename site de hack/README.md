LORIS (Longitudinal Online Research and Imaging System) is a self-hosted web application that provides data- and project-management for neuroimaging research. LORIS makes it easy to manage large datasets including behavioural, clinical, neuroimaging and genetic data acquired over time or at different sites.

A demo instance is available at https://demo.loris.ca.

This Readme covers installation of the LORIS v20.* release on Ubuntu. (CentOS Readme also available).

Please consult the LORIS Wiki Setup Guide notes on this Install process for more information.
Heroku

You can try LORIS on Heroku before installing it on your system. The project management and clinical data management functions of LORIS are available for experimenting with. Imaging functionality is not yet available.

Deploy and log in with username admin and the password that's set up during deployment via ClearDB.

Deploy
Installation
System Requirements

    Apache 2.4 or higher
    MySQL >= 5.7 (or MariaDB >= 10.3)
    PHP 7.2 or higher
    Composer

Composer should be run with --no-dev option unless you are an active LORIS developer.

These dependencies are subject to change so be sure to verify your version of MySQL and PHP when updating LORIS.
Install Steps

Consult the LORIS Wiki page on this Install process for more information.

    Set up LINUX user lorisadmin and create LORIS base directory:

    sudo useradd -U -m -G sudo -s /bin/bash lorisadmin
    sudo passwd lorisadmin
    su - lorisadmin

    Important ⇾ All steps from this point forward must be executed by lorisadmin user

    sudo mkdir -m 775 -p /var/www/$projectname
    sudo chown lorisadmin.lorisadmin /var/www/$projectname

    $projectname ⇾ "loris" or one-word project name

    Get code: Download the latest release from the releases page and extract it to /var/www/$projectname

    Run installer script to install core code, and libraries. The script will prompt for information and so that it can create directories automatically.

    For more information, please read the Installing Loris wiki page.

    cd /var/www/$projectname/tools
    ./install.sh

    Apache configuration and restart LORIS requires Apache's mod_rewrite module to rewrite its URLs. Enable this module, then restart Apache:

    sudo a2enmod rewrite
    sudo service apache2 reload

    Go to http://localhost/installdb.php and follow the instructions to finalize LORIS installation.

    Note: Apache config files will be installed as *.conf, per Ubuntu 14.04. If running an earlier version of Ubuntu, rename these files, then run the following commands. After, restart Apache.

    sudo a2dissite default
    sudo a2ensite $projectname

    Follow the Setup Guide in the LORIS Wiki to complete your post-installation setup and configuration, and for more documentation.

