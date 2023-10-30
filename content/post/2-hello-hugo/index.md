+++
title = "Hello, Hugo!"
subtitle = "About my decision to start blogging again. Now, with Hugo."

date = 2019-02-03
draft = false

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Gabi Udrescu"]

summary = "First real blog post with Hugo"

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["deep-learning"]` references 
#   `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
# projects = ["internal-project"]

# Featured image
# To use, add an image named `featured.jpg/png` to your project's folder. 
# [image]
  # Caption (optional)
#  caption = "Image credit: [**Tenor**](https://tenor.com/view/cat-car-excited-smile-pet-gif-5570235)"

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
#  focal_point = ""

  # Show image only in page previews?
#  preview_only = false

# Set captions for image gallery.

[[gallery_item]]
album = "gallery"
image = "https://media1.tenor.com/images/9123451f0b0d908cdc60dfa5fc9a36d5/tenor.gif?itemid=13366779"
caption = "Default"

[[gallery_item]]
album = "gallery"
image = "https://media1.tenor.com/images/2a5662a25de3a724f5ac08965d275233/tenor.gif?itemid=5734766"
caption = "Ocean"

[[gallery_item]]
album = "gallery"
image = "https://media1.tenor.com/images/119dd3797490c22e49cf42e5357fb719/tenor.gif?itemid=4233186"
caption = "Forest"
+++

<div class="tenor-gif-embed" data-postid="4481045" data-share-method="host" data-width="100%" data-aspect-ratio="1.9606299212598424"><a href="https://tenor.com/view/welcome-gif-4481045">Welcome Back - Despicable Me GIF</a> from <a href="https://tenor.com/search/welcome-gifs">Welcome GIFs</a></div><script type="text/javascript" async src="https://tenor.com/embed.js"></script>

## **A bit of history**

Hello there! I haven't done this for a while now and I guess I've become a little bit rusty. I first started my blog in 2007, on Softpedia.com. It was a very popular forum back in the days, since Facebook was still young and the adoption in Romania was very low.

Soon after, I bought myself a domain and ended up wasting my teenager time on writing various stuff I was very proud of.

Even if now, thinking about it in retrospective, I realise that all that time could have been used for something else, _je ne regrette rien_, as it allowed me to learn a lot of stuff about how to build and maintain a website, be part of a community.

And I've also met hell lot of people. It was probably one of the best decisions I took. 

Fast forward a few more years, I decided that I have more important stuff to do instead of just write random thoughts on the internet. I began to read more and the more I read, the more I realised the little I know and felt that I should only start writting when I know enough.

I'm not saying that now I know everything (although, I do :smile:), but I feel more confident in publishing here bits of text.

## **Why Hugo**

One of the biggest drawbacks on restarting my blogging habbit was the idea that I have to maintain my own blogging infrastructure. Domain, server, PHP, MySQL, Wordpress, plugins, security updates, themes, customizations, scalability... all that made me reluctant on going down this path again.

I was always afraid that if I setup my own infrastructure on DigitalOcean it will never be good enough to keep my blog online on a big traffic spike. Nor it will be unhackable. 

I kinda overcame these fears, but still, too lazy to do it.

A few weeks ago I realised that lots of personal web pages are online through Jekyll and GitHub Pages and I started doing some research on static page builders served through serverless infrastructure.

And so I discovered [Hugo](https://gohugo.io/) and fell in love with the [Academic theme](https://sourcethemes.com/academic/) (I'm currently using, btw). It was the perfect setup for me - in terms of features.

Hugo was simple enough to allow me to bootstrap a blog, while geeky in the same time, keeping me interested. And having everything in plain text makes it really really really portable. 

## **Stack setup**

So, I have my domain using DigitalOcean DNS because, sometimes, when I'm doing some experiments, I want to have a public CNAME for that. The content is hosted on GitHub and deployment is handled automatically with Netlify.

Netlify is a CI/CD service, similar to Travis CI but better integrated with Hugo, doing a very good job for static websites. Less configuration to write than for Travis. 

Initially, I wanted to use Netlify CMS, a Javascript application that is offering a CMS interface for your github website repository, once you get everything up and running. 

But ended up using Sublime (at least for now).

## **How it works**

- create a folder
- create a file with .md extension
- copy the template from a previous post
- start writting
- check everything locally it works well
- git commit & git push

and in 30 seconds it's done. I have posted a new blog post or a modification to my website. This strategy is called [JAMStack](https://jamstack.org/). You can read more about how it works for a big site like SmashingMagazine [here](https://www.netlify.com/blog/2017/03/16/smashing-magazine-just-got-10x-faster/).

## **Drawbacks**

Well, I have to manually add when the post was published. And I don't (yet) have fancy CMS, with WYSIWYG, powerfull galleries or various features that don't really matter.

You need to understand how Git works, if you don't want to use the edit screen in GitHub (that does not have autosave, like Wordpress).

And you don't have custom emails for your domain. Unless you use something like [ForwardEmail](https://forwardemail.net).

## **What do you have available to play with**

1. a personal website that I built in a couple of days, withouth writting a single line of code
1. a blog
1. with photo gallery
1. that I don't have to worry about hosting or technical infrastructure
1. that is not vendor locked
1. [I can do slides in plain text]
1. I can announce [future events] I'm attending or that I'm organizing
1. I don't have to rely on 3rd parties I don't control in order to manage my online presence (LinkedIn, Facebook etc.)
1. a place where I can write tutorials 
1. something to brag about
1. a new toy I can play with
1. emojy :heart: :smile:

Speaking of gallery (confidently click one of the gifs below):


And code syntax highlighting:

```php

<?php

$foo = new Bar();

if($foo->isGreat())
{
  echo 'trully is great!'
}

```

```sql

select * from cms where type = 'static' and rating = 'awesome'

```

And social media posts updates:

{{< tweet 1087652274942431233 >}}
