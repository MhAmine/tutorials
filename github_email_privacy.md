Github email privacy
================

By default, your email is publicly associated with every commit you make. To keep your email private, you will have to navigate to your email settings (more detail on that [here](https://help.github.com/articles/setting-your-commit-email-address-on-github/)):

1.  Click on your profile picture in the top right corner and click *Settings* from the drop-down bar
2.  Click *Emails* from the list of options on the left side-bar.
3.  Check the box next to "Keep my email address private." You can additionally choose to "Block command line pushes that expose my email."

If you decide to keep your email private, you have the option of using a github-provided email address (e.g. <25118334+isteves@users.noreply.github.com>) for your commits/other Github operations.

If you've already set your email on git on your computer, you'll now have to change it. From RStudio, you can easily open it up using *Tools* &gt; *Shell*.

Type `git config user.email` to check out the email address associated with your current project. Simply type your new email after the command to change it: `git config user.email NEWEMAILHERE`. If you want to change your email settings for all projects/accounts, then type `git config --global user.email NEWEMAILHERE`.

All set! ...or are you? If you get an email error next time you try to push changes to your repo, you may have committed some changes with your private email before changing it to the github email address. That also means you checked the button next to "Block command line pushes that expose my email" earlier.

There are a number of [Stack Overflow answers](https://stackoverflow.com/questions/3042437/change-commit-author-at-one-specific-commit). Since I only needed to change one commit, I went with: `git commit --amend --author="Author Name <email@address.com>"`. In the process, I realized that I like to spell amend with to m's, so make sure you double/triple-check your spelling!

Another trick I learned along the way is that if you type in `git` by itself, the screen will populate with a list of possible commands to choose from. It's a useful way to learn a bit more about the commands you're using!
