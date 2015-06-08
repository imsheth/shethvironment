# envinstaller
This is the repo for updating my current pc configuration, which works fine on ubuntu 14.10. Currently a text file, which may be converted into a shell script in future, if needed.

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