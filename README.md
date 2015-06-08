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
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer

# Install gufw
sudo apt-get install gufw

# Disable shopping suggestions
gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"

# Remove shopping suggestions for shopping/amazon
sudo apt-get autoremove unity-lens-shopping

# Install rar
sudo apt-get install rar

# Install git
sudo apt-get update
sudo apt-get install git

# Install curl
sudo apt-get install curl

# Install guake
sudo apt-get install guake

# Install gksu (GKSu is a library that provides a Gtk+ frontend to su and sudo)
sudo apt-get install gksu

# Install System Load Indicator
sudo apt-get install indicator-multiload

# Install Gpick
sudo apt-get install gpick

# Install Filezilla
sudo apt-get install filezilla

# Guake might fail to launch with the following error message: Guake can not init! Gconf Error.
# Have you installed guake.schemas properly?
# To fix this error, run: (Optional)
# sudo mkdir /etc/gconf/schemas
# cd /etc/gconf/schemas/
# sudo ln -s /usr/share/gconf/schemas/guake.schemas

# Install Atom (Optional)
# sudo add-apt-repository ppa:webupd8team/atom
# sudo apt-get update
# sudo apt-get install atom

# Install restricted extras for media codecs (Optional)
# sudo apt-get install ubuntu-restricted-extras 

# Install flash plugin (Optional)
# sudo apt-get install flashplugin-installer

# Install via ubuntu software center
# Mozilla Firefox
# Dropbox
# VLC
# XBMC

# Install after downloading from website
# Chrome 
# Skype
# Teamviewer