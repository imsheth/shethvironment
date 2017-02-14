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
ls ~/.ssh/*.pub
cat ~/.ssh/id_rsa.pub
```

# Install Google Chrome [Credit] (http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line/79284#79284)
### 64 bit
```
sudo apt-get install libxss1 libappindicator1 libindicator7
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome*.deb
```

### 32 bit
```
sudo apt-get install libxss1 libappindicator1 libindicator7
wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
sudo dpkg -i google-chrome*.deb
```

### If error messages pop up then run the command
```
sudo apt-get install -f
sudo dpkg -i google-chrome*.deb
```

### To start the browser
```
google-chrome
```

### This installs a needed library for Google Chrome, then downloads the latest version of Chrome to a temporary directory and installs it
### During the installation a PPA is added to your system so that Google Chrome receives the latest updates whenever you check for system updates


# Install via ubuntu software center
### Mozilla Firefox
### Dropbox
### VLC
### XBMC
### Skype

# Fix Skype [Credit] (http://askubuntu.com/questions/286233/how-to-add-a-skype-indicator/286436#286436)
### To fix skype missing indicator in tray
```
sudo apt-get install sni-qt:i386
```

# Install after downloading from website
### Teamviewer


====================================================================================================
Installing apache2 [Credit] (http://www.maketecheasier.com/install-and-configure-apache-in-ubuntu/)
====================================================================================================

###### Install Java Development Kit [Credit] (http://stackoverflow.com/a/14788468)

# Installation
```
sudo apt-get install openjdk-7-jdk
```

# Set variables
```
echo "export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64" >> ".profile"
echo "export PATH=\$PATH:/usr/lib/jvm/java-7-openjdk-amd64/jre/bin" >> ".profile"
export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64
export PATH=$PATH:/usr/lib/jvm/java-7-openjdk-amd64/jre/bin
```

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
Installing mariadb [Credit] (https://downloads.mariadb.org/mariadb/repositories/#mirror=bytenet&distro=Ubuntu&version=10.0&distro_release=utopic--ubuntu_utopic)
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
Installing mysql [Credit1] (https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04) [Credit2](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)
====================================================================================================

###### Install mysql
```
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```

###### We need to tell MySQL to generate the directory structure it needs to store its databases and information. We can do this by typing :
```
sudo mysql_install_db
```

###### All running threads (in mysql)
```
mysql > show process list;
```

====================================================================================================
Installing php5 and phpmyadmin [Credit] (http://www.rosehosting.com/blog/how-to-set-up-lamp-linux-apache-mariadb-php-stack-on-debian-wheezy/)
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
Installing nginx [Credit] (https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-14-04-lts)
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
Changing the default webroot for nginx / adding virtual host/s [Credit] (https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-virtual-hosts-server-blocks-on-ubuntu-12-04-lts--3)
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

###### Install nodejs
```
sudo apt-get install python-software-properties python g++ make
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install -y nodejs
```

###### Install sails (May show exit 0 status error, be patient and wait for the prompt to return)
```
sudo npm -g --verbose install sails
```

###### Remove PPA
```
sudo add-apt-repository --remove ppa:chris-lea/node.js
```

###### Create a new app
```
sails new testProject
```

###### Lift the server (serves at http://localhost:1337/ by default)
```
cd testProject
sails lift
```

###### Generate a REST API (serves at http://localhost:1337/user by default) 
```
sails generate api user
sails lift
```

###### If npm fails installing modules
```
sudo rm -r node_modules && npm install
```

====================================================================================================
Installing ionic framework for x68_64 [Credit1](https://blog.nraboy.com/2014/09/install-android-cordova-ionic-framework-ubuntu/) [Credit2] (http://askubuntu.com/questions/554045/java-home-is-set-to-the-wrong-directory) [Credit3] (http://askubuntu.com/questions/175514/how-to-set-java-home-for-java)
====================================================================================================

###### Add i386 architecture
```
sudo dpkg --add-architecture i386
```

###### Android SDK requires some x86 architecture libraries even on x64 system
```
sudo apt-get install -qq -y libc6:i386 libgcc1:i386 libstdc++6:i386 libz1:i386
```

###### Update and upgrade installation
```
sudo apt-get update && sudo apt-get upgrade
```

###### Download latest Android Linux SDK for x64 as of 26-11-2015 to desktop
```
http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz
```

###### Rename downloaded zip to android-sdk.tgz

###### Change pwd to desktop
```
cd ~/Desktop
```

###### Unzip, extract, from Android SDK archive file to /opt
```
sudo tar zxf "android-sdk.tgz" -C "/opt"
```

###### Change pwd to /opt and rename folder
```
cd "/opt" && sudo  mv "android-sdk-linux" "android-sdk"
```

###### Set folder permissions and ownership
```
cd "/opt" && sudo chown root:root "android-sdk" -R
cd "$INSTALL_PATH" && sudo chmod 777 "android-sdk" -R
```

###### Change to HOME
```
cd ~/
```

###### Add Android and NPM paths to the profile to preserve settings on boot
```
echo "export PATH=\$PATH:/opt/android-sdk/tools" >> ".profile"
echo "export PATH=\$PATH:/opt/android-sdk/platform-tools" >> ".profile"
echo "export PATH=\$PATH:/usr/bin/node/bin" >> ".profile"
```

###### Add Android and NPM paths to the temporary user path to complete installation
```
export PATH=$PATH:/opt/android-sdk/tools
export PATH=$PATH:/opt/android-sdk/platform-tools
export PATH=$PATH:/usr/bin/node/bin
```

###### Install JDK and Apache Ant
```
sudo apt-get -qq -y install default-jdk ant --verbose
```

##### If java is properly installed you can find it's location, by using the following command (Don't forget to remove bin/java from the end of the path while putting it into JAVA_HOME)
```
readlink -f $(which java)
```

###### Set JAVA_HOME and PATH based on the default OpenJDK installed
```
echo "export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64" >> ".profile"
echo "export PATH=\$PATH:/usr/lib/jvm/java-7-openjdk-amd64/jre/bin" >> ".profile"
export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64
export PATH=$PATH:/usr/lib/jvm/java-7-openjdk-amd64/jre/bin
```

###### Add JAVA_HOME="/usr/lib/jvm/java-7-openjdk-amd64" to /etc/environment 
```
sudo nano /etc/environment
```

###### Install Apache Cordova and Ionic Framework
```
sudo npm install -g cordova --verbose
sudo npm install -g ionic --verbose
```

###### Reboot, and install platform tools
```
android
```

###### Creating sample app
```
ionic start ExampleProject blank
cd ExampleProject
ionic platform add android
ionic build android
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
Gulp [Credit1](http://www.smashingmagazine.com/2014/06/11/building-with-gulp/) [Credit2](https://markgoodyear.com/2014/01/getting-started-with-gulp/) [Credit3](http://slides.com/contra/gulp#/)
====================================================================================================

###### Install gulp globally
```
sudo npm install --global gulp --verbose
```

###### Install gulp and your required project dependencies in devDependencies
```
sudo npm install --save-dev gulp --verbose
sudo npm install --save-dev gulp-notify --verbose
sudo npm install --save-dev gulp-rename --verbose
sudo npm install --save-dev gulp-stylus --verbose
sudo npm install --save-dev gulp-uglify --verbose
sudo npm install --save-dev gulp del --verbose
```

###### Create a gulpfile.js at the root of your project
```
// Sample gulpfile.js

// Load required gulp modules
var gulp = require('gulp'),
    uglify = require('gulp-uglify'),
    rename = require('gulp-rename'),
    notify = require('gulp-notify'),
    stylus = require('gulp-stylus'),
    del = require('del');

// Defining gulp task for performing cleaning of built files
gulp.task('clean', function(cb) {
    del(['app/*.min.js', 'app/assets/css/build/**/*.css'], cb)
});

// Defining gulp task for uglification/minification of .js files
gulp.task('scripts', function() {
    return gulp.src('app/*.js')
        .pipe(rename({
            suffix: '.min'
        }))
        .pipe(uglify())
        .pipe(gulp.dest('app/'));
        // .pipe(notify({
        //     message: 'Uglification complete !'
        // }));
});

// Defining gulp task to get .styl files and render
gulp.task('styles', function() {
    return gulp.src('./app/assets/css/*.styl')
        .pipe(rename({
            suffix: '.min'
        }))
        .pipe(stylus({
            compress: true
        }))
        .pipe(gulp.dest('./app/assets/css/build'));
        // .pipe(notify({
        //     message: 'Minification complete !'
        // }));
});

// Defining watch task watches specified sources for changes and reloads on change
gulp.task('watch', function() {

    // Watch .js files
    gulp.watch('app/main.js', ['scripts']);

    // Create LiveReload server
    livereload.listen();

    // Watch any files in dist/, reload on change
    gulp.watch(['app/dist/**']).on('change', livereload.changed);

});

// A default task is a gulp that runs when you just run just 'gulp'
gulp.task('default', ['clean'], function() {

    gulp.start('scripts', 'styles');

});
```

###### Run gulp
```
gulp
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
Composer
====================================================================================================

###### Downloading and installing composer
```
sudo curl -sS https://getcomposer.org/installer | php
```

###### Making composer available globally
```
sudo mv composer.phar /usr/local/bin/composer
```

###### Adding to PATH
```
sudo PATH=$PATH:/home/starscream/.composer/vendor/bin/
```

###### Installing or updating dependencies
```
sudo composer install --verbose
sudo composer update --verbose
```

====================================================================================================
Laravel
====================================================================================================

###### Enabling/disabling maintenance mode
```
php artisan down
php artisan up
```

###### Lifting development server and on specific port
```
php artisan serve
php artisan serve --port=8001
```

###### To publish vendor settings (after updating/installing via composer)
```
php artisan vendor:publish
```

====================================================================================================
Couchdb [Credit1](http://devgirl.org/2014/12/30/sync-data-using-pouchdb-in-your-ionic-framework-app/) [Credit2](https://github.com/apache/couchdb-fauxton)
====================================================================================================

###### Install couchdb
```
sudo apt-get install couchdb
```

###### Enable CORS (nodejs required)
```
sudo npm install -g add-cors-to-couchdb
add-cors-to-couchdb
```

###### As a root user, edit /etc/couchdb/local.ini and uncomment the bind_address line.  Also change 127.0.0.1 to 0.0.0.0.  Now everyone can access the database.
```
sudo subl /etc/couchdb/local.ini
```

###### Access via futon
```
http://localhost:5984/_utils/
```

###### Install fauxton
```
sudo npm install -g fauxton
fauxton
fauxton --port=8001
```

###### Start/Stop/Restart couchdb
```
sudo service couchdb start
sudo service couchdb stop
sudo service couchdb restart
```

====================================================================================================
Infinidb export database to remote server
====================================================================================================

###### Generate sql dump on source server
```
mysqldump  --set-gtid-purged=OFF --user=root --host=localhost --protocol=tcp --port=3307 --default-character-set=utf8 --skip-triggers "dbtoexport" > /pathtoexportlocation/dbtoexport.sql
```

###### Compress file on source server
```
tar -zcvf dbtoexport.tar.gz dbtoexport.sql
```

###### Get compressed file on destination server via scp
```
scp  user@127.0.0.1:/pathtoexportlocation/dbtoexport.tar.gz /pathtoimportlocation
```

###### Decompress file on destination server
```
tar -zxvf dbtoexport.tar.gz
```

###### Import into database (assuming dbtoexport exists and is empty)
```
idbmysql  dbtoexport < dbtoexport.sql
```

====================================================================================================
MySQL export database to remote server
====================================================================================================

###### Generate sql dump on source server
```
mysqldump  --set-gtid-purged=OFF --user=root --host=localhost --protocol=tcp --port=3306 --password --default-character-set=utf8 --skip-triggers "dbtoexport" > /pathtoexportlocation/dbtoexport.sql
```

###### Compress file on source server
```
tar -zcvf dbtoexport.tar.gz dbtoexport.sql
```

###### Get compressed file on destination server via scp
```
scp  user@127.0.0.1:/pathtoexportlocation/dbtoexport.tar.gz /pathtoimportlocation
```

###### Decompress file on destination server
```
tar -zxvf dbtoexport.tar.gz

```

###### Import into database (assuming dbtoexport exists and is empty)
```
mysql -u root -p dbtoexport < dbtoexport.sql

```


====================================================================================================
Ubuntu tricks / commands
====================================================================================================

###### Environment Variables [Credit] (https://help.ubuntu.com/community/EnvironmentVariables#A.2BAH4-.2F.profile)
export EDITOR=nano

printenv
printenv TERM
echo $TERM

export LC_ALL=
unset LC_ALL

It is also possible to use the "-n" switch to the export command in order to un-export an environment variable and therefore demote it to become a shell variable while preserving its value.
export -n LC_ALL

Session-wide environment variables
Suitable files for environment variable settings that should affect just a particular user (rather than the system as a whole) are ~/.pam_environment and ~/.profile. After having edited one of those files, you should re-login in order to initialize the variables.

~/.profile
In this file you can also place environment variable assignments, since it gets executed automatically by the DisplayManager during the start-up process desktop session as well as by the login shell when one logs in from the textual console. This is a ~/.profile equivalent of the above example:
export FOO=bar
export PATH="$PATH:$HOME/MyPrograms"

Shell config files such as ~/.bashrc, ~/.bash_profile, and ~/.bash_login are often suggested for setting environment variables. While this may work on Bash shells for programs started from the shell, variables set in those files are not available by default to programs started from the graphical environment in a desktop session.

System-wide environment variables
A suitable file for environment variable settings that affect the system as a whole (rather than just a particular user) is /etc/environment. An alternative is to create a file for the purpose in the /etc/profile.d directory.

/etc/environment

This file is specifically meant for system-wide environment variable settings. It is not a script file, but rather consists of assignment expressions, one per line.


FOO=bar
Note: Variable expansion does not work in /etc/environment.

/etc/profile.d/*.sh

Files with the .sh extension in the /etc/profile.d directory get executed whenever a bash login shell is entered (e.g. when logging in from the console or over ssh), as well as by the DisplayManager when the desktop session loads.

You can for instance create the file /etc/profile.d/myenvvars.sh and set variables like this:


export JAVA_HOME=/usr/lib/jvm/jdk1.7.0
export PATH=$PATH:$JAVA_HOME/bin


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

###### For changing .pem file permissions
```
chmod 400 mykeyfile.pem
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
type prettify, select GitGutter
type prettify, select SideBarEnhancements
type prettify, select AutoFileName
type prettify, select BracketHighlighter
type prettify, select DocBlockr
type prettify, select Babel
```

# Crontab

###### List
```
crontab -l
```

###### Edit
```
crontab -e
```

# SSH Tunneling [Credit] (http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

###### Multiport tunneling (-4 required to force IPv4 - useful for RDP, -L 23305:localhost:3305 is in the form of -L local-port:host:remote-port, -i for private key)
```
ssh -4 -L 23305:localhost:3305 -L 23306:localhost:3306  starscream@127.0.0.1
ssh -4 -L 23305:localhost:3305 -L 23306:localhost:3306 -i private_key.pem starscream@127.0.0.1
```

# Disk commands [Credit1] (https://en.wikipedia.org/wiki/Df_%28Unix%29) [Credit2] (https://en.wikipedia.org/wiki/Du_%28Unix%29)

###### Free space (Display in KB, MB, or GB)
```
df -h
```


###### Usage (The weight (size) of subdirectories under the root directory (-d 1, trailing /) with a sum total at the end (-c), all displayed in human-readable format (-h) without traversing into other filesystems (-x). Useful when /var /tmp or other directories are on separate storage from the root directory:)
```
du --max-depth=1 -c -h
```

# Secure Copy

###### Copy file from server
```
sudo scp starscream@127.0.0.1:/data/filetobecopied.txt /home/Desktop/
```

# Screen [Credit1] (http://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/) [Credit2] (http://stackoverflow.com/questions/3202111/how-to-assign-name-for-a-screen)

###### Installation
```
sudo apt-get install screen
```

###### List all screens
```
screen -ls
```

###### Create a new screen
```
screen -S foo
```

###### Reattach screen
```
screen -r foo
```

###### Detach screen
```
Keypress = Ctrl A D
```

# Finding and deleting files [Credit1] (http://askubuntu.com/questions/377438/how-can-i-recursively-delete-all-files-of-a-specific-extension-in-the-current-di)

###### Delete all files with a specific extension (e.g. .bak) from current directory and all subfolders (Also, make sure that -delete is the last argument in your command. If you put it before the -name *.bak argument, it will delete everything.)
```
find . -name "*.bak" -type f -delete
```

###### To find/see exactly which files you will remove
```
find . -name "*.bak" -type f
```