# osx

### general installations

* install latest java jdk
* install iterm2 terminal (optional)
* install Command Line Tools for your mac version
	install it from apple developer website https://developer.apple.com/downloads, requires login.
* install brew
	`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
* brew install git
* brew install nginx
* brew install postgres
* brew install mongodb
* brew install exiftool
* brew install rbenv
* brew install ruby-build
* brew install redis
* brew install logstash
* brew install imagemagick
* brew install freetds
* OR brew install git nginx postgres mongodb exiftool rbenv ruby-build redis logstash imagemagick freetds
* install Node.js version manager using [n-install](https://github.com/mklement0/n-install)  
	if shell is bash `curl -L http://git.io/n-install | bash`
	if shell is ksh `curl -L http://git.io/n-install | ksh`
	if shell is zsh `curl -L http://git.io/n-install | zsh` 
* now install node 4.2.0 
	`n 4.2.0`
* npm install -g bower
* npm install -g gulp	

---

### Create Project Directories
* `mkdir -p ~/dev/map-project`

### Clone MAP in __~/dev/map-project__
* `git clone git@github.com:MonAlbumPhoto/MAP.git`

### Clone MAP-editor __~/dev/map-project__
* `git clone git@github.com:MonAlbumPhoto/MAP-editor.git`

---

### NGINX Configuration

* Create sites-available directory
	`mkdir /usr/local/etc/nginx/sites-available`
* Create sites-enabled directory 
	`mkdir /usr/local/etc/nginx/sites-enabled`
* Add the following line `include /usr/local/etc/nginx/sites-enabled/*;` at the end of nginx.conf file just before `include  servers/*;`
* Copy the map configuration file in sites-available from [MAP/admin/nginx/map.dev.conf.sample](https://github.com/MonAlbumPhoto/MAP/blob/develop/admin/nginx/map.dev.conf.sample)
* Create symbolic link in sites-enabled go inside sites-enabled directory and exceute this 
	`ln -s ../sites-available/ .`
* Do this to start nginx on boot
	```
	sudo cp /usr/local/opt/nginx/*.plist /Library/LaunchDaemons
	sudo launchctl load -w /Library/LaunchDaemons/homebrew.mxcl.nginx.plist
	
	```	
	### RBENV configuration
	* Append this two `export RBENV_ROOT=/usr/local/var/rbenv` & `eval "$(rbenv init -)"` in
	 	`if bash ~/.bash_profile`
	 	`if zsh ~/.zshrc`
	* reload shell profile by using source command like this
	    ```
	     if bash 
	     	source ~/.bash_profile
	     if zsh 
	    	source ~/.zshrc`	
	    ``` 
#### Once you configured RBENV properly
 	* go to map directory and execute this to install ruby and set 2.2.1 as local version
		`rbenv install 2.2.1`
		`rbenv local 2.2.1` 	
	* before installing bundler restart terminal and check `which gem` returns /usr/local/var/rbenv/shims/gem
	  	if it returns the expected value then install bundler 
	  		`gem install bundler`
	* go to map and execute
		`bundle install`
		`bower install`
		* if there is problem with libv8 execute it in this manner
			`gem install libv8 -v '3.16.14.3' -- --with-system-v8`	
	* go to map-editor and execute	
		`bundle install`  		
		`npm install`






		

