 

# Heroku Deployment
This guide is heavily based on the documentation provided by Travis found at:

https://docs.travis-ci.com/user/deployment/heroku/

Start at "Flick the Travis switch" if you're already completed this guide once before.

## Video
I made this video with Ryan Kuhn. It came out alright but the audio is pretty bad and not everyone is a visual learner so I wrote this guide as well.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=SJY_kbk-YcA" target="_blank"><img src="http://img.youtube.com/vi/SJY_kbk-YcA/0.jpg" 
alt="Travis and Heroku Tutorial" width="240" height="180" border="10" /></a>

## Definitions
* Travis CI or Travis Continuous Integration - Wouldn't it be nice if a computer tracked your project and yelled at you the second you broke any of your tests? This tutorial assumes that you'd say yes.
* Ruby - A programming language, we'll be using its package manager, gem, to install Travis CLI
* Travis CLI or Travis Command Line Interface - Allows you to run Travis commands from CMD or Git Bash, super useful and installing it will save you a lot of time later. I think it's programmed in Ruby.
* Heroku CLI or Heroku Command Line Interface - Like Travis CLI but can be installed right out of the gate. For our purposes, we're using this just to get your API key so very small but like Travis CLI, it'll save you a lot of time later. You do need to login to it just like you have to log in to Git Bash.
* Heroku - Web hosting/database service. The first tier is free, the second tier is $7 per project per month. The following tiers start to get expensive but we won't need them.
The Free tier works well until it comes time to present your final project. They also prorate you to the second so you wouldn't pay for the full $7 if you ran their Hobby Tier for less than a month.

## Make a Travis CI account
https://travis-ci.org/
Sign in through GitHub.

## Make a Heroku CI account
Start at the [Heroku] dashboard to make an account.

## Ruby
To install the Travis Command Line Interface (CLI), we're going to have to first install Ruby:

https://rubyinstaller.org/

After you complete the install wizard you may be prompted to enter a number 1, 2, or 3. Just enter 1 and close out of the window when it says it's done installing.

## Travis CLI
After Ruby is done installing restart Git Bash, then run one of two commands. I used the first one, which is the production version of Travis CLI. You could also use the second command which installs the development version. Since we are developers this may be the better choice.

Use one or the other but not both!
1. `gem install travis -v 1.8.8 --no-rdoc --no-ri`
1. `gem install travis --pre`

## Heroku CLI
https://devcenter.heroku.com/articles/heroku-cli

Pretty easy to install from what I remember. Select the installer for your machine. Once this is finished installing open up the Command Prompt (Windows + R, then enter 'cmd'). Enter the following:
```
heroku login
```
You should then be prompted for your email and password for Heroku. Once you've entered that restart Git Bash again.

## Flick the Travis switch
In [Travis] flick the switch of the GitHub project you want to deploy. If you can't find the page with the switches, hover over your name in the top right and click profile.

## Create Heroku app
Head back to [Heroku] and click create an app. You'll have to give it a unique name. The name you give it will be used in the next step so make sure to hold onto it. We'll call it `HEROKU_APP_NAME`.

## Configure .travis.yml
Back in Git Bash `cd` your way into the directory that you want to deploy. Create a file called `.travis.yml` in the root of your repository. Write to the file in sublime:
```
language: java
```
Then switch back to Git Bash and run the command:
```bash
travis encrypt $(heroku auth:token) --add deploy.api_key
```
Go back into your `.travis.yml` file and add `provider: heroku` and `app: HEROKU_APP_NAME` so your config file looks like:
```yml
language: java
deploy:
  provider: heroku
  app: HEROKU_APP_NAME
  api_key:
    secure: "YOUR ENCRYPTED API KEY"
```

## Brian's special sauce
Travis runs on Linux. Linux requires the gradle wrapper to be executable. This command changes the permissions so it can be executable. Run this in Git Bash
```
git update-index --chmod=+x ./gradlew
```

## Push!
Travis is trigged by pushing to GitHub so if you haven't yet done so it's time to push!

[Heroku]: https://dashboard.heroku.com
[Travis]: https://travis-ci.org
