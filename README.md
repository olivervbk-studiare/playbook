Feel free to create a PR to this repository

# Code

## Markdown

[CheatSheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)


## Screencasts

[RubyTapas](https://www.youtube.com/playlist?list=PLj0t_NS6HQk3OKonthcxgXg4bhsP9KH93) - screencast about ruby

[Destroy all Software](https://www.destroyallsoftware.com/screencasts) - screencast about ruby 




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
  * OBS. The download link seems broken. Use https://github.com/tibbon/ruby-koans instead

3. [Ruby coding style guide](https://github.com/bbatsov/ruby-style-guide)

## React

This is an excellent video introducting React with Rails

[React on Rails conf](https://www.youtube.com/watch?v=kTSsZrub5iE)

# Tools

## Git

### Git setup

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage "reset HEAD"
git config --global alias.lg `log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit`
```

### Autocomplete with Git

* Rodar no terminal:
```bash
brew install git && brew install bash-completion
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

* OU autocomplete: completion.bash  in
https://git-scm.com/book/en/v1/Git-Basics-Tips-and-Tricks
