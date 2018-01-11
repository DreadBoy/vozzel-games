---
title: First alpha build and technology stack
logoIcon: fa-github
share_cover: /2018/01/11/first-alpha-and-tech-stack/thumbnail.png
date: 2018-01-11 19:31:21
---


I just pushed out first alpha build to my mailing list and I think it's time to talk about technology stack that's powering this blog and build distribution.

<!-- more -->

## Website hosting

For my side projects I try to to do things as cheaply as possible even if it means I have to mess with technology for some time before it works as I wish. I also like to have as much control over content and presentation as possible, again at cost of time if it needs to be that way. This means I don't like to use content management systems like Wordpress or Joomla. Yes, they are massively supported, popular and easy to work with. Heck, you can set up free Wordpress blog in under a minute over at [wordpress.com](https://wordpress.com) and you even get great templates to work with. I think that's great for people that don't want to mess with technology, they just want a platform where they can express their thoughts and create content. In the past I've tried using wordpress.com, self hosted Wordpress installation and Squarespace but in the end there was always something I wanted to change but was unable to. That's why I went in completely different direction this time and decided to try out [Hexo](https://hexo.io/). Hexo is open source static site generator that takes your Markdown files and theme and converts them to finished website. This is very different from most of content management systems which generate website on fly. Each time you open an article on Wordpress site, Wordpress will fetch theme and article content from database, join them and display the article. But with Hexo, you need to generate every blog post and every site in advance and then deploy the whole website at once. Both ways are fine, it just depends on what are you looking for. Since I didn't wish to pay for server hosting, pre-generation was the right choice for me.

Once my website was generated, I had to host it somewhere. Since I'm programmer, I was familiar with Github and their Github Pages so naturally they were the first thought that popped into my mind. 🙂 And luckily I wasn't the only one, there's already Hexo plugin that can take your website and deploy it directly to Github Pages, all you have to do is run a command. Great! And since I want this blog to look more serious, I also went over to [Hover](https://hover.com) and connected vozzel.games with deployed page. And that's all there is! I can now host a website with complete control over content and theme with absolutely 0 costs (if you exclude cost of domain).

## Mailing list and build distribution

Mailing lists are vital for any business and gamedev is no exception. I've started building mine by signing up for Mailchimp and included signup form in footer of my website. Since I have complete control over website's theme, I could modify signup form so that fits website's layout a bit better. 😉 And why Mailchimp? I've used it in the past, it seems to work and it's free for small users. Once users sign up to mailing list, I can send them blog post updates, new game builds or little presents only for them. And I can of course notify them when game is released... A couple of days ago I sent them first alpha build which they could download and try out. I did that by simply including `.zip` file into public directory of my blog. I know Github discourages big files and in case that's going to be a problem in the future, I checked out Amazon S3 prices and it seems that I can host 1GB of files for 0.03$ per month. Not really expensive, is it? I wonder if there's any better way to distribute games... Something with automatic updates and unified launcher, maybe?