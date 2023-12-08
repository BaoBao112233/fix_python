# fix_python

itheo.tech, I automate Sh!t


Follow


Install python 3.9 on Raspberry PI
Photo by Harrison Broadbent on Unsplash

Install python 3.9 on Raspberry PI

Theo van der Sluijs's photo
Theo van der Sluijs
·
Dec 28, 2020
·
3 min read

Installing python 3.9 on a Raspberry Pi in a few easy to follow steps in a few lines of code. This guide will help to get Python installed within minutes.

Update! 30 Sept 2021
I’ve written several Python installation articles about installing Python 3.8, Python 3.9.5 and Python 3.9.7. But if you really want to go the easy way, go to my Ultimate Python installation script!

On the first of October 2020 I have written the blog post “Install Python 3.8 on a Raspberry Pi“. That article about how to install Python 3.8 on a Raspberry Pi got a lot of attention. A lot of people read my article an started using Python 3.8. But now there is Python 3.9 so I thought why not write an article on how to install Python 3.9 on a Rasperry Pi!

Raspberry PI What?
The Raspberry Pi is a low cost, credit-card sized computer that you can plug into a computer monitor, mouse and keyboard. It is a capable little device that enables people of all ages to explore computing, and to learn how to program in languages like Scratch and Python. The Raspberry runs on linus and has it’s own distro called Raspberry PI OS.

The **Raspberry Pi OS** is the Foundation’s official supported operating system and comes pre-installed with 2 versions of Python. Last time I checked 2.7.x and 3.5.x. And as you want to develop in Python 3, you need to specify the version of Python you are using each time and that is annoying! So, lets install the 3.9 version and make it your default!

Install Python 3.9 on a Raspberry PI
First make sure you can ssh to your Raspberry Pi. The default SSH user and password on Raspberry Pi OS are:
– login: pi
– password: raspberry

You cannot login to your Raspberry Pi with SSH? Read this!

First install the dependencies needed to build:


COPY

COPY
sudo apt-get update
sudo apt-get install -y build-essential tk-dev libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev
Updating…. this takes a while, grab a coffee and get me one to!!

Next download the latest python version, untar it and compile it.


COPY

COPY
wget https://www.python.org/ftp/python/3.9.0/Python-3.9.0.tar.xz
tar xf Python-3.9.0.tar.xz
cd Python-3.9.0
./configure --enable-optimizations --prefix=/usr
make
Building and compiling python can take a while (depends on the Raspberry Pi you have and the amount of memory). And when done, lets install what was build!


COPY

COPY
sudo make altinstall
Lets do a cleanup and remove the files we don’t need anymore


COPY

COPY
cd ..
sudo rm -r Python-3.9.0
rm Python-3.9.0.tar.xz
. ~/.bashrc
Make Python 3.9 default on Raspberry Pi
Finally! Let’s make Python 3.9 the default version, make aliases by:


COPY

COPY
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.9 1
And verify:


COPY

COPY
python -V
If you still have a 2.x or 3.x version and not the 3.9 version, or when you get an error message do as following.


COPY

COPY
nano ~/.bashrc
Go to the last line (arrow down) and find something like:


COPY

COPY
alias python=/usr/bin/python-xxxxxx
And change this to


COPY

COPY
alias python=/usr/local/opt/python-3.9.0/bin/python3.9
If you cannot find any python related alias in your bashrc file just add the above line to your file.

Do a CTRL+X and CTRL+Y

Then in the terminal do:


COPY

COPY
. ~/.bashrc
This refreshes the bashrc in your terminal

Verify the Python version by:


COPY

COPY
python -V
and hopefully you see:


COPY

COPY
Python 3.9.0
Your are ready to go!

Happy programming!! Questions? Let me know in the comments below!



2



Subscribe to my newsletter
Read articles from itheo.tech, I automate Sh!t directly inside your inbox. Subscribe to the newsletter, and don't miss out.

Enter your email address
SUBSCRIBE
Did you find this article valuable?
Support Theo van der Sluijs by becoming a sponsor. Any amount is appreciated!


Sponsor
See recent sponsors | Learn more about Hashnode Sponsors
guide
PayPal
Raspberry Pi
Written by

Theo van der Sluijs
Theo van der Sluijs
Nerd Herder ☆ Agility Master ☆ Code Monkey ☆ Life Hacker ☆ Sport Billy ☆ Male Human ☆ Married ☆ Dad of 2 ☆ Legendary since '75, The Netherlands


Follow
 
MORE ARTICLES

Theo van der Sluijs's photo
Theo van der Sluijs
Unlocking Pages with Custom User Roles in WordPress
Unlocking Pages with Custom User Roles in WordPress
Hello, fellow WordPress enthusiasts! Have you ever wondered how you can take full control over who g…


Theo van der Sluijs's photo
Theo van der Sluijs
Crafting a Custom WordPress Login Page With Shortcodes
Crafting a Custom WordPress Login Page With Shortcodes
Hello, fellow WordPress enthusiasts! Today, I'm going to share with you a little adventure I embarke…


Theo van der Sluijs's photo
Theo van der Sluijs
Taking Home Assistant Notifications to the Next Level with ntfy.sh
Taking Home Assistant Notifications to the Next Level with ntfy.sh
Hey, everyone! Theo here. If you're into Home Automation as much as I am, you know the value of a go…

©2023 itheo.tech, I automate Sh!t

Archive
·
Privacy policy
·
Terms
itheo.tech, I automate Sh!t
