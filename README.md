%title: iTerm and So Can You
%author: Ustice (Jason Kleinberg)
%date: 2016-09-16

-> Who am I? <-

^

-> [Jason Kleinberg](https://github.com/Ustice).
-> Web developer here at Mobquity.

-------------------------------------------------

-> I use my terminal _every day_...

-------------------------------------------------

-> To run my code...

^
~~~
$ node app
~~~

Hello World

-------------------------------------------------

-> To install packages...

^
~~~
$ npm install lodash
~~~

/repos/iterm-and-so-can-you
└── lodash@4.15.0

-------------------------------------------------

-> To get system information...

^
~~~
$ ipconfig getifaddr en0
~~~

10.227.2.92

-------------------------------------------------

-> And more.

-------------------------------------------------

-> Terminal shells have been around as long as Unix (early 1970s),
^
-> and they're largely unchanged,
^
-> but that doesn't mean that they are static.

-------------------------------------------------

-> This is my prompt.
-> (There are many like it, but this one is mine...)




























⎋

-------------------------------------------------

-> Not what you expected, eh? 😎

-> I have customized my prompt with [Oh My Zsh](http://ohmyz.sh/) and [PowerLevel9k](https://github.com/bhilburn/powerlevel9k).

-------------------------------------------------

-> Your terminal is feature-packed, and fully customizable.

^

-> It's a collection of little tools and utilities that you can mix and match to
-> make your life as a developer *easier*.

-> And I want to share with you a few little gems that I have found/created.

-------------------------------------------------

-> Aliases are the easiest way to start. Is there a command that you type a lot?
^
-> Wish it took fewer keystrokes?
^
-> Alias it!
^

~~~
$ alias gs="git status --short"
$ gs
~~~

M README.md
D logo.txt
M start

-------------------------------------------------

-> Need something a little more complex?
^
-> Functions and scripts have you covered.
^

`gpf` (git push feature)

~~~
#!/bin/zsh

BRANCH=$(git symbolic-ref HEAD --short)

git push -u origin HEAD:${BRANCH}
hub browse
~~~

-> This pushes the current branch to `origin`, updates the tracking branch, and
-> opens the GitHub page in the browser.
^

~~~
function standup(){
  if [ -z "$1" ]; then
    mdless $NOTES -P
  elif [ "$1" == "list" ]; then
    mdless $NOTES -lP --no-color | grep "^ \S" --color=never
  else
    mdless $NOTES -s $1 -P
  fi
}
~~~

More on this in a bit...

-------------------------------------------------

-> imgcat

-> Show images inline in the terminal (inlcuded with [iTerm2](https://www.iterm2.com/))

^

-> With it, I created a little utility to retrieve a weather radar, and give me weather information, right in my terminal.
^

~~~
alias weather="curl -sS http://radar.weather.gov/Conus/Loop/southeast_loop.gif | imgcat && ansiweather"
~~~

-------------------------------------------------

-> [jq](https://stedolan.github.io/jq)

-> `jq` is a JSON processor

^

-> With it, I created a little utility to get the dependencies of a project.
^

~~~
#!/bin/zsh

PROJECT_ROOT=$(git rev-parse --show-toplevel)
cat "${PROJECT_ROOT}/package.json" | jq .dependencies
~~~

-------------------------------------------------

-> [mdless](http://brettterpstra.com/projects/mdless/)

-> `mdless` is a  Markdown viewer for the terminal.

^

-> With it, I have created a To Do list that works across projects.
^

~~~
function standup(){
  if [ -z "$1" ]; then
    mdless $NOTES -P
  elif [ "$1" == "list" ]; then
    mdless $NOTES -lP --no-color | grep "^ \S" --color=never
  else
    mdless $NOTES -s $1 -P
  fi
}
~~~

-------------------------------------------------

-> I'm not an expert at this stuff.
^

-> And this is just a *tiny* glimpse into the power of your terminal.
^

-> There are people here that are *way* more advanced than me,
-> but I hope that this has at least inspired you to take a second look at what
-> you can do in your shell.

-------------------------------------------------

-> Want to see how I did all of this?

-> Got an idea on how to make it better? Send me a pull request!

-> https://github.com/Ustice/iterm-and-so-can-you

-> https://github.com/Ustice/dotfiles
