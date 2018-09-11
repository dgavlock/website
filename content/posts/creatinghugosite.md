+++ 
draft = false
date = 2018-09-11T17:10:51-04:00
title = "Creating a Hugo Site with GitHub Pages"
slug = "creatinghugosite" 
tags = []
categories = []
+++



# Quick Backstory

So I've just begun my journey as a web developer and I was stumbling along trying to create a website when I came across an awesome static site generator called Hugo! 

**This is my first post so I hope it's useful** :)

# What is Hugo?

Hugo self-proclaims that they are the "fastest framework for building websites," and I have to say they've made the task pretty simple even for a beginner like me! After a bit of trial-and-error, and some youtubing I was able to get a site up and running on GitHub Pages very quickly! With that said, there were some things I found unclear so I'm going to attempt to write a step-by-step of what I went through to help others have a smoother time getting their website up and running!

# Introduction & Necessary Installations 
**Note: If you have Homebrew and Go skip to [here](#Getting-started-with-Hugo), also if you haven't [configured git](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) or have a [github](https://github.com/) account please do both of those things. Use the email you used to create a github account to configure git!**

## Installing Homebrew

**Note: If you have Homebrew you can skip to downloading go**

I'm going to start with no assumptions here so we will begin by having you install homebrew for MacOS which is super simple and makes life with other tasks way more simple later!Open the terminal by pressing Command + Space and typing "terminal" then pressing enter, then copy and paste the following (You should be in your Home directory):


```
 /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

You'll want to accept any prompts that are thrown and BAM! done! You can now get brewing! (Note: Check out [Homebrew](https://brew.sh/) which is where I got this code). This will make the next couple steps much nicer!

## Installing Go

**Note: If you have Go already installed go ahead and skip this as well!**

Now that you have homebrew, to install Go you will need to type the following into the terminal:

```

brew install go

```

Again, accept any prompts until the download is complete and you will end up with Go installed! If you don't know what Go is it's a programming language created by Google, which is becoming more popular everyday, Hugo will leverage this language to create the website framework. If you are interested in more about Go, [Go here](https://golang.org/doc/) (Pun intended)


# Getting started with Hugo

If you are here you should have the following installed:
* Homebrew
* Go 

## Installing Hugo

Now for installing Hugo, as you might have guessed installing Hugo is just as simple as the previous two installs. Simply type the following:

```
brew install hugo

```

That's it! we are ready to begin working with Hugo!


## Setting up for Hugo

Let's set up a directory to do all our work in. In your terminal go to your home directory by typing the following: 


`cd ~`


then to make a directory name "Sites" type: `mkdir Sites`

move into that directory `cd Sites`

Now that you're in the Sites directory you can now begin to work with Hugo here.
The first step is really simple type:


```

hugo new site yoursitename

```


The hugo new site command will will create the skeleton of your site. You should see the following prompt after you execute the command 

```
Congratulations! Your new Hugo site is created in /Users/YourName/Sites/yoursitename.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.


```
These direction are the next steps you need to take to get your site where you want it. We are going to go over them lightly so you can understand what these components are and how to interact with them. Now you should `cd yoursitename` and then `ls` to check out the directory and you will see the following:

```
archetypes content layouts static config.toml themes data
```

This is the skeleton of your Hugo site, it is here where you will work with creating new content for your site which I've cover once we get your site posted to GitHub. The important thing to notice here is the `theme` directory. The theme directory is where you will be customizing your site.

## Hugo Themes

Hugo allows you to create your own themes or download pre-made open source themes that others have made! The pre-made options are perfect for getting started with Hugo so that's the route we are going here. 

The premade themes can be found at the [Hugo Themes](https://themes.gohugo.io/) page. 

Pick a theme. 

(for the tutorial you will see the Coder theme that I used for my site).
{% github luizdepra/hugo-coder %}

Once you pick a theme click download on its page which will bring you to its github repository. Once there click the green "clone or download" button **Note: make sure you click "Use SSH" on the popup box** then copy the SSH key. Now that you have copied the SSH key go back to your terminal, make sure you are in the `themes` directory type `git clone` and press `control + v` to paste it into the terminal, then enter! **Note: if you do not have git configured check [this](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) article out** Now you should have a repository with the name `coder` or whatever theme you chose; `cd coder` and then 'ls' to see the content of the directory.

These are all the files you will need to make your site look just like the theme you chose! Now `cd exampleSite` and check out the files there.

Now, the easiest way I found to get your site up and running quickly is to take the files from `exampleSite` and replace them with the files you created when you ran the `hugo new site sitename` command. In other words, move everything from `content` in the `exampleSite` directory into the `content` under the `yoursitename` directory. So you will do that for all the files in the `exampleSite` directory until that directory is completely empty. Anywhere that there's duplication like the `config.toml` file remove the one created by the `hugo new site` command. Then move everything else out of the coder directory even if it doesn't have a matching place just move it up out of coder and into youwebsitename directory. The only files you don't need to move are:


```
theme.toml README.md Makefile LICENSE.md

```
**It is extremely important that you move everything correctly!** 

Once you have done that go to the config.toml file and look around. it should look like this (without the notes I have added to the right with the <- before it telling you what to change in the file to customize the website) if you use the coder theme. 

### **Important: You need to change the baseurl to what is specified below!**

```
baseurl = "http://examplesite" <- Change to http://yourgithubusername.github.io

title = "johndoe" <- Name your website here

theme = "hugo-coder" 

languagecode = "en" 

paginate = 20
canonifyurls = true

pygmentsstyle = "b2"
pygmentscodefences = true
pygmentscodefencesguesssyntax = true

disqusShortname = "yourdiscussshortname" <- Your short name for commenting

[params]
    author = "John Doe" <- Your name
    description = "John Doe's personal website" <- How you would describe the site
    keywords = "blog,developer,personal"
    info = "Full Stack DevOps and Magician" <- A small description of what your are
    avatarurl = "images/avatar.jpg" <- your image
    footercontent = "Enter a text here." <- a footer (quotes are nice)

    hideCredits = false
    hideCopyright = false

    rtl = false

    # Custom CSS
    custom_css = []

[[params.social]]
    name = "Github"
    icon = "fab fa-github fa-2x"
    weight = 1
    url = "https://github.com/johndoe/" <- Change to your Github profile url
[[params.social]]
    name = "Gitlab"
    icon = "fab fa-gitlab fa-2x"
    weight = 2
    url = "https://gitlab.com/johndoe/" <- Change to your GitLab profile url
[[params.social]]
    name = "Twitter"
    icon = "fab fa-twitter fa-2x"
    weight = 3
    url = "https://twitter.com/johndoe/" <- Change to your twitter profile url
[[params.social]]
    name = "LinkedIn"
    icon = "fab fa-linkedin fa-2x"
    weight = 4
    url = "https://www.linkedin.com/in/johndoe/" <- Change to your Linkedin profile url
[[params.social]]
    name = "Medium"
    icon = "fab fa-medium fa-2x"
    weight = 5
    url = "https://medium.com/@johndoe" <- Change to your medium profile url

[[menu.main]]
    name = "Blog"
    weight = 1
    url  = "/posts/"
[[menu.main]]
    name = "About"
    weight = 2
    url = "/about/"
[[menu.main]]
    name = "Projects"
    weight = 3
    url = "/projects/"
[[menu.main]]
    name = "Contact me"
    weight = 5
    url = "/contact/"

[languages]
    [languages.en]
        languagename = "English" # The language name to be displayed in the selector.
        title = "John Doe"

        # You can configure the theme parameter for each language.
        [languages.en.params]
        author = "John Doe" <- Your name
        info = "Full Stack DevOps and Magician" <- What you do
        description = "John Doe's personal website" <- quick description
        keywords = "blog,developer,personal"

        [languages.en.menu] # It is possible to change the menu too.

        [[languages.en.menu.main]]
        name = "About"
        weight = 1.0
        url = "/about/"

        [[languages.en.menu.main]]
        name = "Blog"
        weight = 2.0
        url = "/posts/"

        [[languages.en.menu.main]]
        name = "Projects"
        weight = 3
        url = "/projects/"
        [[languages.en.menu.main]]
        name = "Contact me"
        weight = 5
        url = "/contact/"

------------------------delete below (unless you know polish) ----------------
    [languages.pl]
        languagename = "Polski"
        title = "John Doe po polsku"

        [languages.pl.params]
            author = "John Doe"
            description = "Strona domowa John'a Doe"
            keywords = "blog,developer,strona domowa"
            info = "Full Stack DevOps i Magik"

        [languages.pl.menu]

            [[languages.pl.menu.main]]
            name = "O mnie"
            weight = 1.0
            url = "/pl/about/"

            [[languages.pl.menu.main]]
            name = "Blog"
            weight = 2.0
            url = "/pl/posts/"

            [[languages.pl.menu.main]]
            name = "projektowanie"
            weight = 3
            url = "/projektowanie/"
            [[languages.pl.menu.main]]
            name = "kontakt"
            weight = 5
            url = "/kontakt/"
-------------------------------------------------------------------

```

Save the file with your changes. Now go to your terminal and go to the directory `yoursitename`

## Hosting Your Hugo Site Locally

Now that you made the basic changes to the website it's time to host your website on a locally! This will allow you to see what your website looks like before you put it on the internet for people to see!

**Make sure your in the directory `yoursitename`** and type

```
hugo server

```

read the instructions there and paste the localhost url to your browser!

Presto! You have your own website! Congratulations! All the links should work and have the `exampleSite` post and info in them! If they don't you'll want to check and make sure you moved everything correctly outside of the `exampleSite` directory.

Now that you have an awesome site go to the `about.md` file and write about yourself then refresh you browser on the about page. You should see that the website updates automatically in your browser! This is really handy for prototyping posts! Play around with the files a bit to begin to understand how things are organized in the directory and how they look on the browser website. Understanding how things are laid out will make using Hugo later much more intuitive. 

## The Basics of Creating New Content

To create a new file in your hugo site is really simple. First, you'll always want to be in your `yoursitename` directory when creating new content then you will always us the `hugo new (contentpathhere)` command. Try making a new post with the following command

```
hugo new posts/firstpost.md

```

Find firstpost.md and edit it with something, then make sure the `draft` setting in the header is changed to `false` instead of `true`. Save that file and go to the browser and refresh the page, then go to blog and BAM! You created your very first post on your site! THis is the basic process for making new post on a hugo site, you should read more about creating new content when your more comfortable with the basics of Hugo!

## Hosting on GitHub Pages

Now that you made the basic site we will host it for everyone to see on GitHub! GitHub provides this service for free so don't worry about paying for a thing!

The first thing you'll want to do is to go to github and create two repositories

    1. A repository with the exact name as your website directory 'yoursitename'
    2. A repository with the name 'yourgithubusername.github.io'

Once you create those repositories grab the SSH key from the repository with the exact name of your website and then go to your site directory `yoursitename` and type `git init` and then type `git add remote` and paste the SSH key after that. Then type `git pull origin master`.

Now `cd ..` to go to the `Sites` directory and type `git clone` and add the SSH key from the 'yourgithubusername.github.io'. Once cloned `cd yoursitename`, type `hugo -d ../yourgithubusername.github.io`. Now type `git add .` and then `git commit -m 'initial commit`, and lastly `git push origin master`. Now go to GitHub and go to the 'yourgithubusername.github.io' repository and click settings scroll until you see the link to your website that says http://yourgitubusername.github.io. You should now see your site on the web here! Congrats! You now served a website on GitHub Pages! Now you can direct your friends, family, and potential employers to this address to show them all the cool things you post and do!

## The End

I hope this was helpful to those looking to create their first website quickly and please feel free to comment with suggested changes or questions! I will help to clarify anything!

Thank you so much for reading my first post!