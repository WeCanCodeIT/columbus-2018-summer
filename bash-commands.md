# Bash Commands

**Replace [sqrackets] with your own words**

## Standard Console Commands
task | command
-----| -------
Make a new directory for your project | `mkdir [new directory name]`
List the contents of the directory you're inside | `ls`
Change directory to a directory that is inside the same one you are | `cd [directory name]`
Go back a directory | `cd ..`
Go back to the root directory | `cd`
Selects previous commands | up arrow key
Returns to a more recent command | down arrow key
Open sublime and create a new file in the current directory (Example: README.me or .gitignore) | `subl [file name]`
Downloads the junit/mockito/hamcrest build.gradle file into your current directory | `curl https://raw.githubusercontent.com/WeCanCodeIT/gradle-scripts/master/junit-with-mockito-and-hamcrest/build.gradle --output build.gradle`
Runs the gradle script, perform before importing to eclipse | `gradle eclipse`

## Git commands
task | command
-----| -------
Make the directory you're inside into a repository | `git init`
Add all files to the next commit that have been changed | `git add .`
Creates a commit of all the previously added files with a message | `git commit -m "[commit message]"`
Upload all commits made since last push to github | `git push`
Establish the url of the github repo you would like to push to | `git remote add [name (recommended: origin)] [github repository URL]`
Adds all changed files and commits them with a message | `git commit -a -m "[commit message]"`

## Examples
Some commands are used in conjunction with each other so here's a couple of common situations:
### Git Cycle
Personally recommend to complete a cycle at least as often as you're passing tests.
1. `git add .`
1. `git commit -m "[commit message]"`
1. `git push`

**OR**
1. `git commit -a -m "[commit message]"`
1. `git push`
### Starting a new repo
This is a big one to reference because its commands are used infrequently compared to the Git Cycle
1. `cd` your way to your `wcci/code/` folder
1. `mkdir [new directory name]` to create the folder for your new repository
1. `cd [new directory name]` moves you into this new repository
1. Download and run your gradle script
    1. `curl https://raw.githubusercontent.com/WeCanCodeIT/gradle-scripts/master/junit-with-mockito-and-hamcrest/build.gradle --output build.gradle`
    1. `gradle eclipse`
1. `subl README.md`
1. `subl .gitignore` (make sure to finish this before starting your first git cycle)
1. `git init`
1. Finally you can import your repo to eclipse
