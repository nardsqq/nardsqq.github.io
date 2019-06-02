---
layout: post
title: win·dows set·up (1)
---

> "Even the simplest tools can empower people to do great things."

The quote itself is easy to understand, but I just really included it because it sounded cool lol.

Anyways, enough with the bad jokes and off we go to build! I'll be sharing my current development environment setup.
It's on Windows so it won't be relevant to most developers because they're most likely using other OS that suits
a developer more (but hey I'm stuck with Windows so deal with it, right? hehe).

To be honest, setting up a development environment on Windows is not that hard (unless you want to feel the same feeling other developers from a different OS then it'll be hard to achieve that). If you're an engineer who's working mostly with backend
or PHP to be specific then it's _ez pz_. A click on that XAMPP or WAMP install button will already take you to places. 
No configurations that usually involves an editor or the terminal will occur. But if you're currently using either 
of the two or something similar, then I'll help you _up_ your game a bit.

I believe most if not all of us developers are required to learn Git or other version control systems so we'll start with setting 
it up on our machine. First we'll navigate to https://git-scm.com/ then on the lower right part of the page, you'll find a
download button for Windows (just click it, the version's not important, take the latest source release and you're good).
After downloading, just use the setup or install wizard provided and I recommend that you use a separate disk for this
or if not, then default to _disk C:_.

Now that we have Git, of course we'll love to have a package manager for our assets, so let's install _Node_ and its package manager.
Proceed to https://nodejs.org/en/ and you'll see two huge buttons saying that they're download buttons for Windows users. I'd recommend choosing the Long Term Support (LTS) release over the other since it's stable and the community's used to it for quite some
time (asking for help will be easier). Afterwards, just do the same process that you did earlier with Git. This already includes
both _NodeJS_ and _NPM_ so no worries.

Then, we'll have a simple recap, you now have your almighty Git with Git Bash and Git CMD, NodeJS and its widely known package manager.
I don't know if you're contented with Windows CMD but I'm not. So, now you're thinking that I'll just recommend Git Bash instead. If
that's what in your head right now, then you're right. But, we'll make it prettier, cause it looks bad as well. So let's go over
to https://hyper.is/ and extend our Git Bash to it. Just click that beautiful _Download Hyper for Windows_ button and install
it like we did earlier. After installation, just start Hyper and then hit `Ctrl + ," on your keyboard to bring out
that juicy configuration file.

After opening the config file, we'll now wrap Hyper around Git Bash, so this one's a bit tricky but it's actually easy to do. So let's
get started. Scroll down until you see this line:

```
// - Example: `C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe`
```

Below it, you'll see the _shell:_ variable, just assign your git-cmd.exe's $PATH and then we'll continue. So in my case, it'll look like
this:

```
// - Example: `C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe`
shell: 'C:\\Program Files\\Git\\git-cmd.exe',
```

Afterwards, scroll down a bit more and you'll see this:

```
// for setting shell arguments (i.e. for using interactive shellArgs: `['-i']`)
// by default `['--login']` will be used
```

We'll use both the _shellArgs:_ and _env:_ variables underneath so read carefully. So we'll have to assign a value to our shell argument variable:

```
// for setting shell arguments (i.e. for using interactive shellArgs: `['-i']`)
// by default `['--login']` will be used
shellArgs: ['--command=usr/bin/bash.exe', '-l', '-i'],
```

Then we'll have to fill the other one:

```
// for environment variables
    env: {
	TERM: 'cygwin',    	
},
```

And that's it! Just refresh or re-open your hyper app and now you can customize it, just go to https://hyper.is/themes if you love
changing themes or go to https://github.com/bnb/awesome-hyper to see the list of awesome hyper plugins.

So that's the part 1 of our setup post, I'll put part 2 on another one since this is really long. See you on part 2!