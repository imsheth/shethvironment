# shethvironment
This is the repo for ishan sheth's development environment configuration, which works fine on ubuntu 14.10. Currently a text file, which may be converted into a shell script in future, if needed.

====================================================================================================
Setting up ubuntu (14.10)
====================================================================================================

# Update and upgrade installation
```
sudo apt-get update && sudo apt-get upgrade
```

# Install python software properties
```
sudo apt-get install python-software-properties
sudo apt-get install -y python-software-properties python g++ make
```

# Install sublime text 3
```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
```

# Install gufw
```
sudo apt-get install gufw
```

# Disable shopping suggestions
```
gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"
```

# Remove shopping suggestions for shopping/amazon
```
sudo apt-get autoremove unity-lens-shopping
```

# Install rar
```
sudo apt-get install rar
```

# Install git
```
sudo apt-get update
sudo apt-get install git
```

# Install curl
```
sudo apt-get install curl
```

# Install guake
```
sudo apt-get install guake
```

# Install gksu (GKSu is a library that provides a Gtk+ frontend to su and sudo)
```
sudo apt-get install gksu
```

# Install System Load Indicator
```
sudo apt-get install indicator-multiload
```

# Install Gpick
```
sudo apt-get install gpick
```

# Install Filezilla
```
sudo apt-get install filezilla
```

### Guake might fail to launch with the following error message: Guake can not init! Gconf Error.
### Have you installed guake.schemas properly?
### To fix this error, run: (Optional)
```
sudo mkdir /etc/gconf/schemas
cd /etc/gconf/schemas/
sudo ln -s /usr/share/gconf/schemas/guake.schemas
```

# Install Atom (Optional)
```
sudo add-apt-repository ppa:webupd8team/atom
sudo apt-get update
sudo apt-get install atom
```

# Install restricted extras for media codecs (Optional)
```
sudo apt-get install ubuntu-restricted-extras 
```

# Install flash plugin (Optional)
```
sudo apt-get install flashplugin-installer
```

# Generate public ssh key
```
ssh-keygen -t rsa -b 2048 -C "contact@imsheth.com"
cd ~/.ssh
cat id_rsa.pub
```

# Install ScudCloud
```
sudo apt-add-repository -y ppa:rael-gc/scudcloud
sudo apt-get update
sudo apt-get install scudcloud
sudo nautilus /usr/share/applications/
```

# Install via ubuntu software center
### Mozilla Firefox
### Dropbox
### VLC
### XBMC

# Install after downloading from website
### Chrome 
### Skype
### Teamviewer

====================================================================================================
Installing apache2 [Reference] (http://www.maketecheasier.com/install-and-configure-apache-in-ubuntu/)
====================================================================================================

###### Install apache2
```
sudo apt-get install apache2
```

###### To prevent Apache from autostart when booting up (Optional)
```
sudo update-rc.d -f apache2 remove
```

###### To restore Apache back to the autostart list (Optional)
```
sudo update-rc.d apache2 defaults
```

###### Enabling mod_rewrite on apache2, for CakePHP (Optional)
```
sudo a2enmod rewrite
```

###### Restart the apache
```
sudo /etc/init.d/apache2 restart
```

====================================================================================================
Installing mariadb [Reference] (https://downloads.mariadb.org/mariadb/repositories/#mirror=bytenet&distro=Ubuntu&version=10.0&distro_release=utopic--ubuntu_utopic)
====================================================================================================

###### Install the repo manager, if not installed (Optional)
```
sudo apt-get install software-properties-common
```

###### Import the GnuPG signing key
```
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
```

###### Create new repository file by running the commands below.
```
sudo subl /etc/apt/sources.list.d/mariadb.list
```

###### MariaDB 10.0 repository list - created 2015-01-26 10:51 UTC
```
http://mariadb.org/mariadb/repositories/

deb http://mariadb.bytenet.in//repo/10.0/ubuntu utopic main
deb-src http://mariadb.bytenet.in//repo/10.0/ubuntu utopic main
```

###### Update system and install mariadb-server
```
sudo apt-get update
sudo apt-get install mariadb-server
```

====================================================================================================
Installing mysql [Reference1] (https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04) [Reference2](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)
====================================================================================================

###### Install mysql
```
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```

###### We need to tell MySQL to generate the directory structure it needs to store its databases and information. We can do this by typing :
```
sudo mysql_install_db
```

====================================================================================================
Installing php5 and phpmyadmin [Reference] (http://www.rosehosting.com/blog/how-to-set-up-lamp-linux-apache-mariadb-php-stack-on-debian-wheezy/)
====================================================================================================

###### Install php5
```
sudo apt-get install php5 libapache2-mod-php5 php5-mysql
```

###### Install phpmyadmin
```
sudo apt-get install phpmyadmin
```

###### Answers to prompts
###### 1. Web server to reconfigure automatically: answer ‘apache2′.
###### 2. Configure database for phpmyadmin with dbconfig-common? – answer ‘NO’.

###### Copy over the the PHPMyAdmin Apache conf file over to the conf-available directory (for mysql)
```
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
```

###### Enable the Apache conf file using a2enconf (for mysql)
```
sudo a2enconf phpmyadmin
```

###### Change default listening port

###### Edit 
```
sudo subl /etc/apache2/ports.conf
```

###### Change 
```
Listen 80
```

###### Edit 
```
sudo subl /etc/apache2/sites-enabled/000-default.conf
```

###### Change 
```
Listen 80
```

====================================================================================================
Changing the default webroot for apache 2
====================================================================================================

###### Include the following line in /etc/apache2/apache2.conf 
```
Include /etc/phpmyadmin/apache.conf
```

###### 1. /etc/apache2/sites-enabled/000-default.conf

###### change
```
/var/www/html
```

###### to (folder required to be existing)
```
/home/starscream/public_html
```

###### 2. /etc/apache2/apache2.conf file

###### change
```
<Directory /var/www/>
 Options Indexes FollowSymLinks
 AllowOverride None
 Require all granted
</Directory>
```

###### to
```
<Directory /home/starscream/public_html>
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>
```

###### 3. Configuration for CakePHP, all following lines too (Optional)
```
<Directory />
    Options FollowSymLinks
    AllowOverride All
</Directory>

<Directory /home/starscream/public_html>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Order Allow,Deny
    Allow from all
</Directory>
```

###### Take ownership and hange file permissions of webrooot

====================================================================================================
Installing nginx [Reference] (https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-14-04-lts)
====================================================================================================

###### Install nginx
```
sudo apt-get update
sudo apt-get install nginx
```
###### We can make sure that our web server will restart automatically when the server is rebooted by typing
```
sudo update-rc.d nginx defaults
```

###### This should already be enabled by default, so you may see a message like this:
System start/stop links for /etc/init.d/nginx already exist.

###### This just means that it was already configured correctly and that no action was necessary. Either way, your Nginx service is now configured to start up at boot time.

====================================================================================================
Changing the default webroot for nginx / adding virtual host/s [Reference] (https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-virtual-hosts-server-blocks-on-ubuntu-12-04-lts--3)
====================================================================================================

###### Add entry in hosts
```
sudo subl /etc/hosts


127.0.0.1	localhost
127.0.1.1	starscream
127.0.0.1	angular.example.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

###### Create virtual host by configuring server block
```
sudo subl /etc/nginx/sites-enabled/example

server {
  listen 80;
  server_name angular.example.com;
  root /home/starscream/public_html/example_web;
  index app/index.html;
  location /{
      try_files $uri /app/index.html;
  }
}
```

###### Create a link and reload server
```
sudo ln -s example /etc/nginx/sites-available/example
sudo service nginx reload
```


====================================================================================================
Installing node.js and sails.js
====================================================================================================

###### Install nodejs
```
sudo apt-get install python-software-properties python g++ make
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install -y build-essential
```

###### Install sails (May show exit 0 status error, be patient and wait for the prompt to return)
```
sudo npm -g --verbose install sails
```

###### Remove PPA
```
sudo add-apt-repository --remove ppa:chris-lea/node.js
```

====================================================================================================
Bower
====================================================================================================

###### Installing bower
```
sudo npm install -g bower --verbose
```

###### Interactively create a bower.json with bower init
```
bower init
```

###### Install package and add it to bower.json dependencies
```
bower install <package> --save
```

###### Install package and add it to bower.json devDependencies
```
bower install <package> --save-dev
```

====================================================================================================
Grunt
====================================================================================================

###### Install grunt cli
```
sudo npm install -g grunt-cli --verbose
```

====================================================================================================
Yeoman
====================================================================================================

###### Install yeoman
```
sudo npm install -g yo --verbose
```

====================================================================================================
Stylus
====================================================================================================

###### Install stylus
```
sudo npm install stylus -g --verbose
```

###### Compiles stylus file (to compressed file.css)
```
stylus -c file.styl
```

###### Compiles stylus file (to compressed file.css)
```
stylus file.styl
```

====================================================================================================
AngularJS
====================================================================================================

###### Installing angularjs
```
bower install angular
```

====================================================================================================
Ubuntu tricks / commands
====================================================================================================

###### Popup notification
```
sudo apt-get install libnotify-bin
notify-send 'Title of the message' 'Text of the message'
notify-send -i /home/sathiya/deal.ico 'Deal success'
notify-send -u critical -i "notification-message-IM" 'Boss !!' 'Am done with the execution'
command && notify-send
```

###### Lock screen
```
gnome-screensaver-command --lock
```

###### For taking file ownership
```
sudo chown -R starscream: /opt/lampp/htdocs/Dropbox/xampp-root
```

###### For changing file permissions
```
sudo chmod -R 777  /opt/lampp/htdocs/Dropbox/xampp-root
```

###### Start apache2
```
sudo /etc/init.d/apache2 start 
```
or
```
sudo service apache2 start
```

###### Stop apache2
```
sudo /etc/init.d/apache2 stop   
```
or
```
sudo service apache2 stop
```

###### Restart apache2
```
sudo /etc/init.d/apache2 restart 
```
or
```
sudo service apache2 restart
```

###### Start/restart/stop/reload configuration nginx
```
sudo service nginx start
sudo service nginx restart
sudo service nginx stop
sudo service nginx reload
```

###### Run jasmine tests
```
jasmine-node --matchall test/store.test.js
```

###### To open terminal before login
```
^ + Alt + F2
```

###### To reset unity
```
dconf reset -f /org/compiz/
unity --reset-icons
```

###### Reinstall Unity in Ubuntu 14.04 to fix system freeze issue
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo shutdown -r now
```

###### Fixing Unity freeze issue with Nvidia graphics
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo apt-get remove --purge nvidia*
sudo shutdown -r now
```

###### Prettify package for Sublimetext

https://packagecontrol.io/installation
```
Ctrl+Shift+P or Cmd+Shift+P in Linux/Windows/OS X
type install, select Package Control: Install Package
type prettify, select HTML-CSS-JS Prettify
```
