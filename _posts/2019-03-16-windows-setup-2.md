---
layout: post
title: win·dows set·up (2)
---

_Phew_, Another month passed before this one. I have to apologize to myself 😂

I've been busy this past month and a lot of things happened but that's for a separate post (next to this). Right now, my goal is to finish this two part blog post so we can finally move on to my Object Oriented Programming posts.

So, let's start!

On our [last post](https://blog.nardsparagas.com/windows-setup-1/), we've basically prepared our Windows machine to have a basic set of tooling (NPM, Git, and Hyper) and to add up, we'll start by downloading a code editor. We'll use [Visual Studio Code](https://code.visualstudio.com/) for this one, and don't jump to any conclusions just yet. You have all the power to pick your own poison. May it be a flexible editor or a very powerful IDE, it's really up to you.

Anyhow, let's proceed by [downloading vscode](https://code.visualstudio.com/download), it supports most known platforms so no worries about that. But since we're on Windows and this is a Windows setup tutorial, we'll go for that attractive purple button that has **Windows** all over it. Afterwards, just like what we did with our previous installers, just follow through the install wizard and you're good to go.

VSCode is incredibly flexible like Sublime Code and has a lot of open source packages that the community built and contributed into. It's already great upon startup that most of the interns from our company just starts writing code on it immediately without even adding _batteries_ to it or changing its default theme. Which kinda makes me cringe by the way, I don't hate the default color of the editor but knowing that you can improve it easily and you chose not to just gets in my head sometimes. 😅 But that's just an opinion, as I've said earlier, you can do whatever you want with your tools.

Here's some of the most notable plugins that I install on my VSCode:

* Auto Comment Blocks - for Javadoc-style multi-line comments and single-line comment blocks
* File Utils - easily create, duplicate, move, and rename files on the go
* GitLens - explore your files and you'll be able to see who wrote that faulty code a month ago 😂
* Material Icon Theme - one of the best icon themes developed, it just suits any of the editor's theme
* markdownlint - who told you that you don't have to lint your markdown files?

Now we're done adding the _batteries_, it's time to setup our development environment.

I mostly work with PHP, Javascript, and the Laravel framework at work. I just recently picked up NodeJS so I've tried to look for a more powerful and flexible local development server other than the usual portable XAMPP. After pulling my hair out by trying out Laradock or running Docker Desktop for Windows to manage my containers, I've finally decided to just stick with a plug and play client called [Laragon](https://laragon.org/). Aside from being built on top of the all time familiar WampServer, it's also adaptable to change. You can just add a new package or application within and you'll be able to use it together. You can also check the testimonials page on their website to know more about the said local development environment.

It comes out of the box with different databases, a _quick create_ functionality that allows you to install fresh projects, an intuitive dashboard, and the reliable cmder as terminal. But these are not the reasons that made me do the switch from Laradock, what it gave me really is its _Pretty URLs_ or the _Auto Virtual Hosts_ feature. You can easily create a fresh project within the `laragon\www\` directory and Laragon will generate a pretty url for you. So if you have a fresh project named _to-do-app_, you'll have: `to-do-app.test` by default but you can easily change that through the `Menu > Preferences` tab.

That's all I can offer for now, if you'd like to know more about Laragon, you check can out their [documentation](https://laragon.org/docs/).

In the future, I'll also write a more detailed step-by-step guide using the updated Windows Subsystem for Linux for Windows 10 machines together with _oh-my-zsh_, _Vim_ as our primary editor, and make it more flexible like an actual unix based machine.

Thank you for reading!
