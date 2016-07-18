# Setting up environment on Mac

1. Install Xcode from the App Store

2. Once installed, go to Preferences -> Locations tab, and check if you already have Installed the Command Line Tools component. If not, install it from Apple's developer page or type gcc in a bash terminal to call the Command Line Developer Tools Installer.

3. Install HomeBrew and gcc-42

  ```bash
  ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"
  OR
  ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go/install)"
  ```

  ```bash
  brew tap homebrew/dupes
  brew install apple-gcc42
  ```

4. Install rvm ( http://rvm.io ) - this will allow you to manage ruby and gem versions. It also installs a gui called Jewelry

  ```bash
  \curl -L https://get.rvm.io | bash -s stable --ruby
  ```

  ###### TO START RVM:

    ```bash
    source /Users/felipeam/.rvm/scripts/rvm
    ```

  Run the following to install current version of ruby:

  ```bash
  rvm install 2.3.0
  rvm use 2.3.0
  rvm --default 2.3.0
  ```

5. Install rails

  ```bash
    gem install rails
    ```

( alternatively you could try  http://railsinstaller.org/en#osx - not recommended)
(If you are receiving an error changing group of /opt/rix to rvm just restart the pc.

6. Install RubyMine IDE (there is a free trial for 30 days)
 https://www.jetbrains.com/ruby/download/index.html

7. Create ( if you don't have one ) account at github. (optional) You can also install the github app (https://mac.github.com)

8. Case has been installed github, download the repository (click the button Clone in Desktop) - this will open the github app for mac. You should now be able to see the repository in your github app.

9. (optional) Install pry. Pry is a better repl than irb

  ```bash
   $ sudo gem install pry   
  ```

10. Install postgresql from home-brew

  * install:

    ```bash
    brew install postgresql
    ```

  * init db (maybe)

    ```bash
    initdb /usr/local/var/postgres -E utf8
    ```

  * start postgres server ( to test it in ruby mine)

    ```bash
    postgres -D /usr/local/var/postgres
    ```

11. Setup your git environment. CHANGE THE COMMAND LINES BELOW

  ###### CONFIG

    ```bash
      $ git config --global user.name "Your Name Here"
      $ git config --global user.email "your_email@example.com"
    ```

  ###### PASSWORD CACHING

    ```bash
      $ ssh-keygen -t rsa -C "MY@EMAMAIL.COM"
    ```
    After run the command above, you will be asked for a key name. You can leave this question in blank, but is recommended that you change this name to avoid conflicts. Put a name (with the right path) like `~/.ssh/id_rsa_git` for example. If you want, leave next questions in blank by hitting enter for all of then.
    You will have created `.ssh/id_rsa_git` and `.ssh/id_rsa_git.pub` files.

    Use `ssh-add ~/.ssh/id_rsa_git` to add keys, `ssh-add -l` to check saved keys and `ssh-add - D` to delete all not used cached keys.

    Another recommendation is to create a config file to manager multiple git keys. It will be useful for github and heroku. At ~/.ssh/ create a config file like below:

    ```
    #git rodrigo's mac account
    Host github.com-activehacker
      HostName github.com
      User git
      IdentityFile ~/.ssh/id_rsa_git
    ```

    Now "cat" the id_rsa.pub file content and copy the text exactly from the first "s" in "ssh-rsa" to the last character in your email and paste it in github.com/settings/ssh, click "Add SSH Key" in the top right, enter in a Title and then paste into the Key field. Hit "Add SSH Key".

    At last, run the command below to check connection.

    ```bash
      $ ssh -T git@github.com
    ```

  ###### ADD REPOSITORIES (git clone)

  ```bash
    git remote add origin git@github.com:felipeamaraldemattos/kroton-engenharias.git
    git remote add heroku git@heroku.com:studiare.git
    git remote add heroku-staging git@heroku.com:studiare-staging.git
  ```

12. Install heroku toolbelt from https://toolbelt.heroku.com

  ```bash
    heroku login
    ssh-keygen -t rsa
    heroku keys:add ~/.ssh/key_filename.pub
  ```
  `ssh-keygen -t rsa` will generate a ssh public key file **id_rsa.pub**. As we did in github configuration, create a ssh key file like `~/.ssh/id_rsa_heroku`.
  You can check existing keys and remove old ones using the commands below:

  ```bash
    heroku keys
    heroku keys:remove rodrigoprates@Rodrigos-Mac-mini.local
  ```

  Finally, add some lines in config file, as we did in github configuration.

  ```
  #heroku rodrigo's mac account
  Host heroku.com
    HostName heroku.com
    IdentityFile ~/.ssh/id_rsa_heroku
    IdentitiesOnly yes
  ```

  Validate with `ssh -v git@heroku.com`.

13. Choose your Editor:
  * [RubyMine](https://www.jetbrains.com/ruby/)
  * [Sublime Text](https://www.sublimetext.com/3)
  * [others](http://stackoverflow.com/questions/826164/a-definitive-list-of-ides-for-ruby-on-rails)  

14. Restore the database:
  * Save the file (.dump) in a folder like: `yourUser/dev/kroton_engenharias_dev_db/dumps/a182.dump`
  * Then run this command: `pg_restore --verbose --clean --no-acl --no-owner -h localhost -U felipeam -d kroton_engenharias_dev_db dumps/a182.dump`, where you must change `felipeam` by your userName.

15. In Rubymine, use the rakes:
  * db:create
  * db:repopulate
  * db:migrate

16. You need parallelism!

  a. Install Redis:

    ```bash
    brew install redis
    ```

  b. Start Redis:

    ```bash
    redis-server
    ```

  c. Install and start Sidekiq:

    ```bash
    gem install sidekiq
    bundle exec sidekiq
    ```

17. Develop
  * Before development you have to:
    ** Start postgres: `postgres -D /usr/local/var/postgres`
    ** Start Redis: `redis-server`
    ** Start Sidekiq: `sidekiq` or `bundle exec sidekiq`
    ** Update your code: `git pull origin master`
    ** Update your Gem repo: `bundle install`
    ** Update your npm repo: `npm install`
    ** Run db:migrate: `rake db:migrate` or `ActiveRecord::Migrator.migrate "db/migrate"` 

###### APPS

  * Google Play

  * cordova build --release android

  * jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore

  * CordovaApp-release-unsigned.apk studiare

  * zipalign -v 4 CordovaApp-release-unsigned.apk Studiare.apk
