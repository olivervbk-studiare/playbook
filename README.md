Feel free to create a PR to this repository 

# Code 

## Markdown 

[CheatSheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Ruby

**Tip:** Always which you want test anything in Ruby, run the command prompt below:

  ```bash
  irb
  ```

1. Short Introduction to ruby [RubyMonk](https://rubymonk.com/)

2. Excellent guide to grok main nuances/details in Rub language [RubyKoans](http://rubykoans.com/)
  * Recommendation: If you prefer which after each change make in your editor the koans run again automatically, install Ruby gem called **watchr**. See below:

  ```bash
  cd ruby_koans
  rake
  gem install watchr
  watchr koans.watchr
  ```

OBS. The download link seems broken. Use https://github.com/tibbon/ruby-koans instead

# Tools 

## Git

### Git setup 

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage "reset HEAD"
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### Autocomplete with Git 

autocomplete: completion.bash  in 
https://git-scm.com/book/en/v1/Git-Basics-Tips-and-Tricks


