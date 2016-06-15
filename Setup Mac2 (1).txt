Setting up environment on Mac


1. Install Xcode from the App Store

2. Once installed, go to Preferences -> Downloads -> Install Command Line Tools

3. Install HomeBrew and gcc-42

ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"
OR 
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go/install)"


brew tap homebrew/dupes
brew install apple-gcc42
sudo ln -s /usr/local/bin/gcc-4.2 /usr/bin/gcc-4.2

4. Install rvm ( http://rvm.io ) - this will allow you to manage ruby and gem versions. It also installs a gui called Jewelry

\curl -L https://get.rvm.io | bash -s stable --ruby
TO START RVM:
source /Users/felipeam/.rvm/scripts/rvm

Run the following to install current version of ruby
rvm install 2.0.0
rvm use 2.0.0
rvm --default 2.0.0

5. Install rails 
gem install rails
  ( alternatively you could try  http://railsinstaller.org/en#osx - not recommended)
  (If you are receiving an error changing group of /opt/rix to rvm just restart the pc.

6. Install RubyMine IDE ( there is a free trial for 30 days)
 https://www.jetbrains.com/ruby/download/index.html

7. Create ( if don't have one ) account at github. (optional) You can also install the github app http://https://mac.github.com ) 

8. Download the repository ( click the button Clone in Desktop - this will open the github app for mac 
 You should now be able to see the repository in your github app. 

9. (optional) Install pry. Pry is a better repl than irb 
 $ sudo gem install pry   

10. Install postgresql from home-brew

  * install: 
	brew install postgresql
  * init db (maybe) 
	initdb /usr/local/var/postgres -E utf8
  * start postgres server ( to test it in ruby mine)
	postgres -D /usr/local/var/postgres

11. Setup your git environment. CHANGE THE COMMAND LINES BELOW 

   CONFIG

 $ git config --global user.name "Your Name Here"
 $ git config --global user.email "your_email@example.com"

   PASSWORD CACHING
 $ ssh-keygen -t rsa -C “MY@EMAMAIL.COM”
   now “cat” the file and copy the text exactly from the first “s” in “ssh-rsa” to the last character in your email and paste it in github.com/settings/ssh, click “Add SSH Key” in the top right, enter in a Title and then paste into the Key field. Hit “Add Key”.
 $ ssh -T git@github.com

ADD REPOSITORIES (git clone)
git remote add origin git@github.com:felipeamaraldemattos/kroton-engenharias.git
git remote add heroku git@heroku.com:studiare.git 
git remote add heroku-staging git@heroku.com:studiare-staging.git 

12. Install heroku toolbelt 
  from https://toolbelt.heroku.com 

  configure heroku 
heroku login
ssh-keygen -t rsa
heroku keys:add


13. In Rubymine, use the rakes : 
  * db:create
  * db:repopulate
  * db:migrate

14. Develop

15. You need parallelism!

a. Install Redis:
brew install redis

b. Start Redis:
redis-server

c. Start Sidekiq (after installing the Gem - gem install sidekiq)
bundle exec sidekiq



APPS

Google Play

cordova build --release android

jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore 

CordovaApp-release-unsigned.apk studiare

zipalign -v 4 CordovaApp-release-unsigned.apk Studiare.apk
