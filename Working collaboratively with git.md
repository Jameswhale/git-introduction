# Working collaboratively with git

## 1. Create a new repository
First you will need to login to GitHub and create a new repository. Navigate to your homepage and click on the repositories tab. Click on the green 'New' in the top right of the page. Enter a name for your repository e.g. 'your-name'-git-intro. Tick the box to initialize this repository with a README, then hit 'Create Repository'

## 2. Clone your repository
Now you need to copy your new repo so you can work on it locally. You do this by cloning it. You can clone the repository by clicking on the green 'Clone or download' button and copying the URL it provides. First navigate to the directory where you would like to clone the repository to. Then in a terminal (mac) or Git BASH (windows) type the following:
```
git clone < paste the URL here >
``` 
Once the repository has downloaded there should be a new directory there with the name of your repository.

## 3. Make a new file
Next you are going to add a new file to our repo. There are lots of ways to do this but here is an easy way:
```
echo "Hello World!" > helloworld.txt
```
This will create a new .txt file with `Hello World!` in it.

## 4. Adding a new file
Now you have created a new file you need to add it to your repository. First let's see what creating that new file has done to your branch. By typing `git status` you can see the status of your branch. Doing this now will return something like this:
```
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        helloworld.txt

nothing added to commit but untracked files present (use "git add" to track)
```
So you have to add the file to your commit. You do this using the following command:
```
git add helloworld.txt
```

Running `git status` again now should now show this:
```
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   helloworld.txt
```
This tells us that your new file has been added and it is ready to commit

## 5. Committing the file

Now you have added the file you need to actually commit the change. To do this use the `git commit` command. If you use the commit command like this it will open a text editor where you can make a multiline commit. However for a small change you can use the `-m` option. This allows you to add a short message to your commit:
```
git commit -m "Adding helloworld file"
```
Using the `git status` command you can now see what doing the commit has done. You should see something like this:
```
On branch master
Your branch is ahead of 'origin/master' by 1 commits.
  (use "git push" to publish your local commits)
```
Now you have made our commit you need to push it from your computer to the remote repository. This is done by using `git push`
You will do this by typing the following:
```
git push origin master
```
This is telling git to push your commit to the master branch on the remote server (known as `origin`). GitHub might ask you for your username and password here, if so just enter them to complete the commit.

Now that we have pushed our change, let's see what that's done to our repository on GitHub. Go to your GitHub account repository page and look at the repository you created earlier. You should now see the new file you created in the repository!


## 6. Working on a public repository
Up to now you have been working on your own repository, but what about working with others?
For the next few steps you will need to find a partner and work through the steps together. That will allow you to try out creating and reviewing pull requests and resolving merge conflicts.

## 7. Make a fork from their repository
Once you have teamed up with somebody you will need to get a copy of their repository. To do this you will need to go to their GitHub page and find their repository. Once you have found their repository click the button in the top right of the page which says 'Fork'. This will create a copy of their repository in your account.

## 8. Clone the fork
Once you have a copy of their repository in your account, you can make a local copy by cloning it in exactly the same way as you did before with your own repository (look back at step 2).

## 9. Make a change to a file with a mistake
Now that you have a copy of their repository you are going to make a change to the helloworld.txt file. However this time you are going to deliberately make a mistake! Open the helloworld.txt file in a text editor and add a new line to the file with some obvious mistakes. E.g.
```
I knwo hwo to use gti!
```

## 10. Add the change - this time with patching!
Now you will commit the change just like before, however this time instead of adding the file you can use this command:
`git add -p`
The `-p` option stands for `patch`. The advantage of this option is that it lets you review your changes as you add them to a commit. You will see something like this:
``` 
Hello World!
+I knwo hwo to use gti!
\ No newline at end of file
Stage this hunk [y,n,q,a,d,/,e,?]?
```
Lines starting with a `+` symbol are new lines being added and a `-` for lines being removed.
The final line is git asking you what it should do with this chunk of code. There are quite a few options here, but the main ones you will use are `y` for yes and `n` for no. Normally you would probably spot the error above and decide not to add it to the commit, but for this exercise we will pretend we missed it so hit `y` then `enter` to add the line. 
I like this command as it gives you the opportunity to review your changes as you commit and spot any errors before you make a pull request. It can be a real timesaver for you and your team when doing code reviews as you can catch simple errors easily before the pull request. There is one main drawback of this command in that it doesn't work for brand new files, only changes to existing files. You will have to add new files by using `git add <filepath>` just like you did earlier.

## 11. Commit the change
Now you can commit the change using `git commit -m "<your message here>"`
You can then push the commit using `git push origin master` and you are then ready to make a pull request.

## 12. Make a pull request to their repository
Go back to GitHub and go to your partner's repository and click on the 'Code' tab. Find and click the button on the left-hand side titled 'New pull request', this opens the page where you can make a pull request. 
First you will need to click on the link 'compare across forks' so you can compare your version of the repository with theirs. In the middle of the page you should now see four dropdown menus 'base fork', 'base', 'head fork', and 'compare'. The base fork should be populated with your partner's version of the repository `their name/repository name` and the base populated with `master`. For the head fork you should be able to select your version of the repository from the dropdown: `your name/repository name`. Compare should also be set to `master`. 
As you do this you should see the frame in the middle of the page change to a text field and a larger text frame below it. You may notice that the text field is already populated with the message we made when we our commit. The text box is for adding additional longer commit messages.
Below the text box the page will show a comparison showing all the commits in this pull request and also shows all the changes to files that will be made. Here you should be able to see the change we made to the helloworld.txt file. Once you're happy with the content of the pull request hit the 'Create pull request' button. Once again we will deliberately ignore the mistake in the file.


## 13. Review the pull request
Now that the pull request has been made it's over to your partner to review the change, and to decide if it should be approved and merged into the repository.
To do this they should go to the repository on their GitHub page and click on the 'Pull request' tab. There they will see the pull request you just made. They can see the commit message you wrote, the commit you made and the files you changed and they can now review your pull request. So now over to your partner to review your code!

As the reviewer it is your responsibity to check the content of the pull request and spot any mistakes or to suggest improvements etc.
Now because you are an eagle-eyed developer(!) you will have surely spotted the typo that your partner made in the helloworld file. So now we have to inform them of their mistake by leaving a comment on the pull request or even better on the file (and even the line) of the error. To do this mouse over the line where their error is just to the right of the line number. A blue cross should appear, clicking it will bring up a text box where you can explain the error. Once you have finished reviewing all the files in the pull request you then need to decide if it should be merged or not.
Considering the errors in the helloworld file we definitely don't want to merge this change to our repository, therefore we will  click on the 'Review changes' drop down on the 'file changes' tab and select 'request changes'. 
This will reject the pull request and notify your partner that is was rejected. 

## 14. Fix the error
Oh dear, so our pull request was declined! However thankfully our partner has helpfully pointed out what the mistake we made was and even what line it was on! So now we need to make those changes. Open the helloworld.txt file and make the suggested changes to fix the typos we originally made. 

## 15. Commit the change and update the Pull Request
Once that's done, we add, commit and push the change as we did before, however this time we don't need to create a new pull request as our earlier one is still open the new push will just update the existing one. 

## 16. Approve the Pull Request
With the pull request updated it can be reviewed again, and assuming the change has now been fixed the pull request can be accepted. Once again click on the 'Review changes' dropdown though this time you can select 'approve'.

## 14. Merge the Pull Request
Back on the 'Conversation' tab you should now see a green button 'Merge pull request', hit this, then 'Confirm merge' to merge the pull request. 

## 15. Swap roles and repeat steps 7-14 
Now that you have successfully made and updated a pull request, swap roles with your partner and repeat steps 7-14 so they can try making the pull request and you can try reviewing one. 

## 16. Merge conflicts
Now that there has been multiple developers working on your repository you are in a position to create and resolve a merge conflict.
This task can be done on your own but it does require that you have completed the pair work beforehand for it to work.

Open helloworld.txt that you create back in step 4 of this workshop. Despite the changes that were made to this file during the pair work, the copy of this file stored locally on your laptop won't have any of these changes in it so it should just contain one line 'Hello World!'. This is because we haven't pulled those changes from the github repository yet (we won't do it now as this will prevent us from getting the merge conflict).
Edit helloworld.txt by adding `I'm making a merge conflict!` on a new line, then add and commit the change as before. 
Now when you try to do `git push origin master` you should see this:
```
To https://github.com/Jameswhale/git-introduction.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/Jameswhale/git-introduction.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
This is telling you that there are some changes on the remote master branch that aren't on your local master branch. To solve this we need to pull those changes down to our local branch you do this with `git pull`
You shoud see something like this:

```
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 4 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (4/4), done.
From https://github.com/Jameswhale/git-introduction
   f6361e6..4246770  master     -> origin/master
Auto-merging test.txt
CONFLICT (content): Merge conflict in test.txt
Automatic merge failed; fix conflicts and then commit the result.
``` 
This tells us that there was a merge conflict,  git was unable to resolve it automatically and that we will have to fix it manually. 
To fix the confict we will need to open the file and work out what the conflict is:
```
Hello World!
<<<<<<< HEAD
I'm making a merge conflict!
=======
hello to you too
>>>>>>> 4246770bb7045b30e70b7e512079aecad87dcaad
```
This looks a bit confusing so what does it mean?
```
<<<<<<< HEAD
I'm making a merge conflict!
```
This is the change you just made. HEAD is the current position on your branch.
```
hello to you too
>>>>>>> 4246770bb7045b30e70b7e512079aecad87dcaad
```
This is the change made on the remote branch. The long string of numbers and letters is the unique identifer for the commit, so we don't need to pay attention to it now. `=======` is just a divider between the two commits. 

The content of the merge conflict will influence how we resolve the conflict. We might want to keep both lines, we might want to keep one, not the other, or we might need to combline the two lines in some way. To keep it simple in this example we will keep both lines, your local change first then the remote change second. To do this we will delete these three lines: 
```
<<<<<<< HEAD
=======
>>>>>>> 4246770bb7045b30e70b7e512079aecad87dcaad
```
So that the file now looks like this:
```
Hello World!
I'm making a merge conflict!
hello to you too
```
Save the file and then use `git add` and `git commit` to complete the merge.
If you use the `git status` comand now it should return something like this:
```
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
The two commits are our original commit and the commit we made when fixing the merge conflict. We can now push these commits as normal.
