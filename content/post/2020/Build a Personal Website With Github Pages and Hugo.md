

+++

author = "Gwen G."

comments = true

date = "2020-03-21"

draft = false

image = "/content/images/hugo.jpg"

menu = ""

share = true

slug = "HUGO_GitPages"

tags = ["tech"]

title = "Build a Personal Website With Github Pages and Hugo"

summary = 'Build personal website with hugo'

+++



# Build a Personal Website With Github Pages and Hugo

![hugo](/content/images/hugo.jpg)

A personal webpage is a perfect place to let the world know about you and showcase your past accomplishment. Put your resume, your projects, your blogs on with a personalised theme which makes people know you have a great taste: all-in-one! It's your portfolio displayed online, a small yet cool project you can do with not much effort, why not?

With Github Pages, we can host a personal webpage without bothering about finding a domain name, and with Hugo, we have a variety of themes to choose from. This tutorial uses a Mac OS and will run several command line in terminal: don't worry, it's absolutely a tutorial for starters! Now, let's start this step-by-step tutorial to set up you personal webpage! 



## Introduction to HUGO and GitPage

Hugo is one of the most popular open-source static site generators and is written in GO. It's simple, efficient, easy to scale, and fast to deploy. Simply install with brew, clone themes you like from Github or from the official website [HUGO](https://gohugo.io/), make some changes in the configuration file and the deploy, then your page will be online. 

[Github Pages](<https://pages.github.com/>) is a static web hosting service provided by github, which provides 1GB of free space and provides convenient deployment directly through the github repository.

This site uses Hugo and Github Pages to create and deploy. The following briefly introduces the deployment process.



## STEP 1. Installation

**Install Hugo**

Open your terminal, run the following command line one by one:

```
brew install hugo
```

To check whether you installed hugo successfully, enter the following into your terminal

```hugo version
hugo version
```

And when the version displayed as shown in this screenshot, success! 

![image-20200320212313656](/content/images/image-20200320212313656.png)



**Install Git**

Hugo also recommends installing Git, to check if you have it on your computer, run:

```
git --version
```

If you've installed it, it shows your version of git, if not, it will prompt you to install it automatically.



Finish? Let's move to next step!



##STEP 2. Build your site locally

Now let's build a site locally on your computer first.

**Set up the site**

The first step is to go to the directory where you want to save your website, I want to create my site on my desktop, so run the following command in terminal:

```
cd /Users/geyuanyuan1/Desktop
hugo new site mysite
```

Then, you'll see as the following screenshot, and a folder called "mysite" is already on your desktop!

![image-20200320215047104](/content/images/image-20200320215047104.png)



The folder structure will look like this:

![image-20200320215209195](/content/images/image-20200320215209195.png)

What are these files/ folders used for?

The ones we will work with:

- config.toml : the configuration file, we will need to edit it later.
- content : stores all the content of the website, including all of your blog posts, resumes and so on, can include folders, but usually all `.md` files.
- static : Stores static files such as your background pictures, logos, css, js, etc. The files in this directory will be directly copied to it `/public`. This folder has higher priority than the `/static`folder under the theme.
- themes : now it's empty, but will save the theme of your choice later.

The others, but we will not use them in this tutorial: 

- archetypes : stored `.md`template files, it has higher priority than `/archetypes`folders under the theme.

- data : stores data files for template calls

- layouts : store `.html`templates, this folder has higher priority than `/layouts`folders under the theme

Also, there will be a "public" folder created when you want to deploy the website:

- public : After executing the `hugo`command, store the generated static file

**Choose a theme**

Pick a theme you like from the official website [Hugo themes](<https://themes.gohugo.io/>) or from Github ( You can find the source themes from people's Repository)!

Here I used this theme which was based on the "casper" theme and edited by  @[vjeantet](https://github.com/vjeantet/hugo-theme-casper/commits?author=vjeantet).

Run the following command line in you terminal:

```
cd mysite
cd themes
git clone https://github.com/vjeantet/hugo-theme-casper
```

Or, a simple way is to download the entire repository and replace the "themes" folder!



**Edit config.toml**

Now let's set up some configuration, open the "mysite" folder and open "config.toml" with your text editor.

It only has three lines now as following:

![image-20200320222212886](/content/images/image-20200320222212886.png)



Don't worry, go to where you found the theme and find some sample repositories, here I went back to @[vjeantet](https://github.com/vjeantet/hugo-theme-casper/commits?author=vjeantet)'s sire repository [vjeantet.fr](https://github.com/vjeantet/vjeantet.fr) to find his "config.toml", copy all the contents into our local file, and do some customized edit.

A configuration example as following:

```
baseurl = "https://[your github username].github.io/"
languageCode = "en-us"
title = "the website title shown on the tab"
theme = "the same as theme name (exactly the folder name) in your themes folder"
paginate = 2
Copyright = "© Yuanyuan GE 2020"
canonifyurls = true

[params]
  description = "Enter your personal description"
  cover = "images/cover.png" 
  ##save the image you want to use as background picture in directory "./static/images"
  author = "author name"
  authorlocation = "authorlocation"
  logo = "images/logo.png" 
  ##save the image you want to use as website logo in directory "./static/images"
  githubName = "your github name"
  linkedinName = "your linkedin name"
  email = "your email"
  instagramName = "your ins name"
  
  hideHUGOSupport = false

[[menu.main]]  # here are the buttons on the menu 
  name = "Home" # Button will display as "Home"
  weight = 100 # the weight decides the position of the button (higher or lower)
  identifier = "home"
  pre = "<br />" 
  url = "/"

[[menu.main]]
  name = "Contact"
  weight = 0
  identifier = "contact" 
  # this button will refer to a markdown file named "contact" in the content folder
  pre = "<br />"
  url = "/contact"

[[menu.main]]
  name = "Blog"
  identifier = "blog"
   # this page will refer to a markdown file named "blog" in the content folder
  pre = "<br />"
  url = "/post"
  weight = 40
  
[permalinks]
  post = "/:slug/"

[sitemap]
  ChangeFreq = ""
  Filename = "sitemap.xml"
  Priority = "-1"

```

Note that the picture directories and configuration might vary from theme to theme, make sure to read the instruction of the theme you choose.



**Create your first blog**

Then, you can create your first markdown file in the content folder by running:

```
cd mysite
hugo new about.md
```

Or, you can edit the markdown file in your text editor and save it to the content folder!

You need to delete the line "draft=true" to make it shown on your site.

Content of `about.md`will be available at `http://localhost:1313/about`[.](http://localhost:1313/about.)



**Test the site locally**

Run the command:

```
cd mysite
hugo server
```

The terminal will show instruction as this:

![image-20200321005318364](/content/images/image-20200321005318364.png)



Go to http://localhost:1313/ in your web browser and the page is shown!

(Here I didn't put the background image into the ```./static/images``` folder)

![image-20200321005504512](/content/images/image-20200321005504512.png)



## STEP 3. Deploy to Git Pages

**Get the website rendered in the ```public``` folder**

In your terminal, run the following command:

```
cd mysite #(note: here should be 'cd' + the full path to mysite)
hugo
```

Then you'll see a ```public``` folder appears in the ``mysite`` folder, it contains the web files(might include html, css, js, etc.) that Hugo automatically generates.



**Create your Github Repository**

In order to pubish your site with the link ```yourusername.github.io```,  you will need to create a repository named ```<USERNAME>.github.io```.

1. Go to your Github webpage and click on the "New" to create a new repository, contain the fully rendered version of your Hugo website.

![image-20200321164056233](/content/images/image-20200321164056233.png)

2. Then don't initiate with a README.md, click on "Create Repository".

   ![image-20200321171754206](/content/images/image-20200321171754206.png)



   **Go back to terminal and commit**

   In terminal, go to the directory of the ``public`` folder, then run commands:

   ```
   cd public
   git init
   git add .
   git remote add origin https://github.com/username/username.github.io.git
   git commit -m "first commit"
   git push origin master
   ```

   The terminal will display as in the screen shot:

   ![image-20200321174023064](/content/images/image-20200321174023064.png)

   ![image-20200321174043998](/content/images/image-20200321174043998.png)



   (You can directly add all the files in the ``public`` folder (only the files not the entire public folder!) to the repository through github, too.)



   **Go to check your website!**

   After successfully commited, go to your repository and click on the "Settings" on the top right, then scroll down to the Github Pages section.

   When you see the green box, click on the published link.

   ![image-20200321174211212](/content/images/image-20200321174211212.png)

   ![image-20200321174251504](/content/images/image-20200321174251504.png)

   Now the site is successfully published! You can also customize your background image and post new blogs later!

   ![image-20200321174606810](/content/images/image-20200321174606810.png)




## The End

That's all for this tutorial, happy blogging!

If you want to learn more about Hugo or Github, you can refer to the official websites: [HUGO](https://gohugo.io/), [Github Pages](<https://pages.github.com/>)



Know more about me or my projects by following me on [Github](https://github.com/Yuanyuan229), [Linkedin](https://www.linkedin.com/in/yyge/), [Medium](<https://medium.com/@yyge>) or visit my website here: https://yuanyuan229.github.io

