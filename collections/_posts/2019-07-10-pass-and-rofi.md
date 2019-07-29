---
layout:  post
name:    posts
title:   "Pass and Rofi"
created: 2019-07-10
---

# Context

[Last time](/2019/05/12/pass.html) I described how I use
[Pass](https://www.passwordstore.org/), a unix password manager, to add a bit of
convenience and security to my life. Like all things in life, I opted for the
DIY version of a tool that is also commercially available. Why? Because life is
[suffering](https://en.wikipedia.org/wiki/Dukkha)! (If you want to actually know
why then go read the post, it won't take long).

## What are we doing here...?

Well I can't speak for you, but I am trying to have my cake and eat it too. I
want a system that

- is highly (perhaps completely) configurable 
- has no unwanted bells and whistles
- is rippin' fast!
- assumes I know what I'm doing and lets me do it myself

This is why I opt for solutions that often involve a bit more setup. Things that
work out-of-the-box are nice at first, but often leave me wanting more,
navigating through feature bloat, or insecure to a degree that I find
unsettling.

## Enter Rofi

[Rofi](https://github.com/davatorium/rofi) is a wildly useful tool. I use it for
launching applications, opening SSH sessions, and a whole lot more. You can
style it and use it to streamline a lot of workflows. Let's take a look at how
it could help us here.

With Pass, my workflow might look something like this:

- go to website `somesite.com`
- enter username in appropriate field
- open a terminal window
- ponder what folder I saved that password in
- open a terminal
- type `pass find somesite` and hit the return key
- ah... that's where it is...
- execute the full `pass` command to copy the password to my clipboard
- enter my GPG password in the system dialog
- close the terminal window
- go back to the web browser and paste the password

There's a better way!

Rofi is really good at selecting one thing from a list of many. Seems perfect
for this! I'm only trying to streamline the use case for copying an existing
password to the clipboard, so something like [this project that I found](
https://github.com/carnager/rofi-pass) is a bit overkill for my needs (but I dig
that someone did that). The workflow should look as such:

- go to website `somesite.com`
- enter username in appropriate field
- run a script that interacts with Rofi (using a system keybinding)
- type `somesite` or just enough to filter and select the right option
- press enter
- enter my GPG password in the system dialog
- go back to the web browser and paste the password

That's a lot better! Let's see how we can get Rofi to streamline this workflow.

## The Script

Rofi has a `dmenu` option that helps us out tremendously for this use case. From
the documentation:

```
-dmenu

Run  rofi  in dmenu mode. This allows for interactive scripts. In dmenu mode,
rofi reads from STDIN, and output to STDOUT. A simple example, displaying three
pre-defined options:

    echo -e "Option #1\nOption #2\nOption #3" | rofi -dmenu

Or get the options from a script:

    ~/my_script.sh | rofi -dmenu
```

Armed with that knowledge, we can begin writing a script. Let's start by
defining a function that will get the options from Pass:

```
function menu(){
    cd ~/.password-store
    find -iregex .*\.gpg | cut -c 3- | sed s/\.gpg\$//
}
```

This lists all the GPG files in our password store (that is, all the encrypted
passwords) and prints them out in a nice format. The `cut -c 3-` removes the
leading `./` in the file names. The `sed` command replaces any `.gpg` substring
found at the end of the string with nothing.

Like the documentation says, we can Pass that right into Rofi with the `-dmenu`
option.

```
choice="$( menu | rofi -dmenu -i -p 'pass:' -matching fuzzy)"
```

Let's create a variable `choice` to hold what the user chooses. Let's also use
the `-i` flag for a case-insensitive search, the `-p` flag to specify a prompt,
and `-matching` to make the search fuzzy (because fuzzy searches are great when
you organize things deeply in subdirectories like I do).

After that, all we have to do is execute the user's choice (if there is any)
with Pass.

```
# user cancelled - bail with no-op
if [ -z $choice ]
then
    exit
fi

pass -c $choice
```

That's it! The whole script looks like so:


```
#!/bin/bash

function menu(){
    cd ~/.password-store
    find -iregex .*\.gpg | cut -c 3- | sed s/\.gpg\$//
}

choice="$( menu | rofi -dmenu -i -p 'pass:' -matching fuzzy)"

# user cancelled - bail with no-op
if [ -z $choice ]
then
    exit
fi

pass -c $choice

```

## Thanks For Reading!
If you have any questions or improvements please feel free to drop me a line.
You can reach me by sending an email to blog [at] this domain.
