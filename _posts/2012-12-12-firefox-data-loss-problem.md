# firefox data loss problem
 to copy old firefox data on new firefox application 

# Bookmarks, Downloads and Browsing History:

    places.sqlite
    This file contains all your Firefox bookmarks and lists of all the files you've downloaded and websites you’ve visited.
    bookmarkbackups
    This folder stores bookmark backup files, which can be used to restore your bookmarks.
    favicons.sqlite
    This file contains all of the favicons for your Firefox bookmarks. 
    
# Passwords:

    key4.db
    logins.json
    
# Site-specific preferences:

    permissions.sqlite
    content-prefs.sqlite
   
# Search engines:

    search.json.mozlz4
    This file stores user-installed search engines.
    
# Personal dictionary:

    persdict.dat
    This file stores any custom words you have added to Firefox's dictionary.
    
# Autocomplete history:

    formhistory.sqlite
    This file remembers what you have searched for in the Firefox search bar and what information you’ve entered into forms on websites. 
    
# Cookies:

    cookies.sqlite
    A cookie is a bit of information stored on your computer by a website you’ve visited. Usually, this is something like your site preferences or login status. Cookies are all stored in this file.
    
 # DOM storage:

DOM Storage is designed to provide a larger, more secure, and easier-to-use alternative to storing information in cookies.

    webappsstore.sqlite
    Information is stored in this file for websites
    chromeappsstore.sqlite
    This file stores information for about:* pages. 
    
 # Extensions:

    extensions
    This folder, if it exists, stores files for any extensions you have installed.
    
 # Security certificate settings:

    cert9.db
    This file stores all your security certificate settings and any SSL certificates you have imported into Firefox. 
    
 # Security device settings:

    pkcs11.txt
    This file stores security module configuration. 
    
# Download actions:

    handlers.json
    This file stores your preferences that tell Firefox what to do when it comes across a particular type of file. For example, these are the settings that tell Firefox to open a PDF file with Acrobat Reader when you click on it. For 
    
# Stored session:

    sessionstore.jsonlz4
    This file stores the currently open tabs and windows.
    
# Toolbar customization:

    xulstore.json
    This file stores toolbar and window size/position settings.
    
# User preferences:

    prefs.js
    This file stores customized user preference settings, such as changes you make in Firefox Settings dialogs. The optional user.js file, if one exists, will override any modified preferences. 
    
 # Containers:

    containers.json
    This file stores the details of containers used by the Container Tabs feature, including those created by extensions such as Facebook Container. 

# step to move old data to new firefox profile

     cd /home/username/.mozilla/firefox/                  ex: cd /home/james/.mozilla/firefox/
     cd new_profile                                       ex: cd rmrtcu9g.default
     
     sudo rm -rf places.sqlite key4.db logins.json permissions.sqlite search.json.mozlz4 persdict.dat formhistory.sqlite cookies.sqlite cert9.db handlers.json containers.json content-prefs.sqlite extensions extension-settings.json extensions.json extension-store favicons.sqlite
     
     cd ..
     cd old_profile                                       ex: cd 0796e5vp.dev.firefox
     
     sudo cp -rp  places.sqlite key4.db logins.json permissions.sqlite search.json.mozlz4 persdict.dat formhistory.sqlite cookies.sqlite cert9.db handlers.json containers.json content-prefs.sqlite extensions extension-settings.json extensions.json extension-store favicons.sqlite /home/username/.mozilla/firefox/new_profile
     
