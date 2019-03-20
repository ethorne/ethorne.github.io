# Personal Site
## Where can I find this site?
[here](https://erikthorne.com/)

## Thanks to
- The developers at [jekyll](https://jekyllrb.com/) for enabling me to not write
code for a blog
- [Raphaël Moreau](https://github.com/rphlmr/) for making a
[gruvbox theme for jekyll](https://github.com/rphlmr/jekyll-gruvbox-theme)

## Dev
This is for when future Erik decides to write a post on a new machine.

### DO NOT
Do not use apt to install jekyll.

### Install

```
sudo apt install ruby ruby-dev make build-essential
gem install jekyll bundler jekyll-feed
```


make sure this is in your `.bashrc`
```
export GEM_HOME=~/.ruby
export PATH="$PATH:$HOME/.ruby/bin:$HOME/gems/bin"
```

### Run
- clean: `jekyll clean`
- run on localhost: `jekyll serve --incremental`

