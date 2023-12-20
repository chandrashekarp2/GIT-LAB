
Learn Git with Bitbucket Cloud
Objective

Learn the basics of Git with this space themed tutorial. 
Mission Brief

Your mission is to learn the ropes of Git by completing the tutorial and tracking down all your team's space stations. Commands covered in this tutorial:

    git clone, git config, git add, git status, git commit, git push, git pull, git branch, git checkout, and git merge

Time

30 minutes
Audience

You are new to Git and Bitbucket Cloud
Prerequisites

You have installed Git

You have a Bitbucket account
Create a Git repository

As our new Bitbucket space station administrator, you need to be organized. When you make files for your space station, you’ll want to keep them in one place and shareable with teammates, no matter where they are in the universe. With Bitbucket, that means adding everything to a repository. Let’s create one!

Some fun facts about repositories

    You have access to all files in your local repository, whether you are working on one file or multiple files.
    You can view public repositories without a Bitbucket account if you have the URL for that repository.
    Each repository belongs to a user account or a team. In the case of a user account, that user owns the repository. + In the case of a team, that team owns it.
    The repository owner is the only person who can delete the repository. If the repository belongs to a team, an admin can delete the repository.
    A code project can consist of multiple repositories across multiple accounts but can also be a single repository from a single account.
    Each repository has a 2 GB size limit, but we recommend keeping your repository no larger than 1 GB.

Git logo
related material
Git commands
Learn more
Bitbucket logo
SEE SOLUTION
Setting up a repository
Read tutorial
Step 1. Create the repository

Initially, the repository you create in Bitbucket is going to be empty without any code in it. That's okay because you will start adding some files to it soon. This Bitbucket repository will be the central repository for your files, which means that others can access that repository if you give them permission. After creating a repository, you'll copy a version to your local system—that way you can update it from one repo, then transfer those changes to the other.
Central git repo to local git repo

Do the following to create your repository:

1. From Bitbucket, click the + icon in the global sidebar and select Repository.
Select repository from the Bitbucket side navigation

Bitbucket displays the Create a new repository page. Take some time to review the dialog's contents. With the exception of the Repository type, everything you enter on this page you can later change.
Create a new repository config window in Bitbucket

2. Enter BitbucketStationLocations for the Name field. Bitbucket uses this Name in the URL of the repository. For example, if the user the_best has a repository called awesome_repo, the URL for that repository would be https://bitbucket.org/the_best/awesome_repo.

3. For Access level, leave the This is a private repository box checked. A private repository is only visible to you and those you give access to. If this box is unchecked, everyone can see your repository.

4. Pick Git for the Repository type. Keep in mind that you can't change the repository type after you click Create repository.

5. Click Create repository. Bitbucket creates your repository and displays its Overview page.
Step 2. Explore your new repository

Take some time to explore the repository you have just created. You should be on the repository's Overview page:
Repository overview screen in Bitbucket

Click + from the global sidebar for common actions for a repository. Click items in the navigation sidebar to see what's behind each one, including Settings to update repository details and other settings. To view the shortcuts available to navigate these items, press the ? key on your keyboard.

When you click the Commits option in the sidebar, you find that you have no commits because you have not created any content for your repository. Your repository is private and you have not invited anyone to the repository, so the only person who can create or edit the repository's content right now is you, the repository owner.
Copy your Git repository and add files

Now that you have a place to add and share your space station files, you need a way to get to it from your local system. To set that up, you want to copy the Bitbucket repository to your system. Git refers to copying a repository as "cloning" it. When you clone a repository, you create a connection between the Bitbucket server (which Git knows as origin) and your local system.
Bitbucket server "origin" to "local system"
Step 1. Clone your repository to your local system

Open a browser and a terminal window from your desktop. After opening the terminal window, do the following:

1. Navigate to your home (~) directory

 $ cd ~

As you use Bitbucket more, you will probably work in multiple repositories. For that reason, it's a good idea to create a directory to contain all those repositories.

2. Create a directory to contain your repositories.

 $ mkdir repos

3. From the terminal, update the directory you want to work in to your new repos directory.

 $ cd ~/repos

4. From Bitbucket, go to your BitbucketStationLocations repository.

5. Click the + icon in the global sidebar and select Clone this repository.

Bitbucket displays a pop-up clone dialog. By default, the clone dialog sets the protocol to HTTPS or SSH, depending on your settings. For the purposes of this tutorial, don't change your default protocol.
Clone a repository in Bitbucket

6. Copy the highlighted clone command.

7. From your terminal window, paste the command you copied from Bitbucket and press Return.

8. Enter your Bitbucket password when the terminal asks for it. If you created an account by linking to Google, use your password for that account.

    If you experience a Windows password error:
        In some versions of Microsoft Windows operating system and Git you might see an error similar to the one in the following example.

        Windows clone password error example

$ git clone

https://emmap1@bitbucket.org/emmap1/bitbucketstationlocations.git 

Cloning into 'bitbucketspacestation'...

fatal: could not read

Password for 'https://emmap1@bitbucket.org': No such file or directory

    If you get this error, enter the following at the command line:

  $ git config --global core.askpass

    Then go back to step 4 and repeat the clone process. The bash agent should now prompt you for your password. You should only have to do this once.

At this point, your terminal window should look similar to this:

$ cd ~/repos

$ git clone https://emmap1@bitbucket.org/emmap1/bitbucketstationlocations.git
Cloning into 'bitbucketstationlocations'...
Password
warning: You appear to have cloned an empty repository.

    You already knew that your repository was empty right? Remember that you have added no source files to it yet.

9. List the contents of your repos directory and you should see your bitbucketstationlocations directory in it.

$ ls

Congratulations! You've cloned your repository to your local system.
Step 2. Add a file to your local repository and put it on Bitbucket

With the repository on your local system, it's time to get to work. You want to start keeping track of all your space station locations. To do so, let's create a file about all your locations.

1. Go to your terminal window and navigate to the top level of your local repository.

 $ cd ~/repos/bitbucketstationlocations/

2. Enter the following line into your terminal window to create a new file with content.

$ echo "Earth's Moon" >> locations.txt

If the command line doesn't return anything, it means you created the file correctly!

3. Get the status of your local repository. The git status command tells you about how your project is progressing in comparison to your Bitbucket repository.

At this point, Git is aware that you created a new file, and you'll see something like this:

$ git status 
 On branch main
 Initial commit
 Untracked files:
   (use "git add <file>..." to include in what will be committed)
     locations.txt
 nothing added to commit but untracked files present (use "git add" to track)

The file is untracked, meaning that Git sees a file not part of a previous commit. The status output also shows you the next step: adding the file.

4. Tell Git to track your new locations.txt file using the git add command. Just like when you created a file, the git add command doesn't return anything when you enter it correctly.

$ git add locations.txt

The git add command moves changes from the working directory to the Git staging area. The staging area is where you prepare a snapshot of a set of changes before committing them to the official history.
Working directory to Staging Area

5. Check the status of the file.

 $ git status 
 On branch main
 Initial commit
 Changes to be committed:
   (use "git rm --cached <file>..." to unstage)
     new file: locations.txt

Now you can see the new file has been added (staged) and you can commit it when you are ready. The git status command displays the state of the working directory and the staged snapshot.

6. Issue the git commit command with a commit message, as shown on the next line. The -m indicates that a commit message follows.

$ git commit -m 'Initial commit' 
 [main (root-commit) fedc3d3] Initial commit
  1 file changed, 1 insertion(+)
  create mode 100644 locations.txt

The git commit takes the staged snapshot and commits it to the project history. Combined with git add, this process defines the basic workflow for all Git users.
Staging area to commit history

Up until this point, everything you have done is on your local system and invisible to your Bitbucket repository until you push those changes.

    Learn a bit more about Git and remote repositories
        Git's ability to communicate with remote repositories (in your case, Bitbucket is the remote repository) is the foundation of every Git-based collaboration workflow.
        Git's collaboration model gives every developer their own copy of the repository, complete with its own local history and branch structure. Users typically need to share a series of commits rather than a single changeset. Instead of committing a changeset from a working copy to the central repository, Git lets you share entire branches between repositories.

Three repositories with arrows pointing between them all

    You manage connections with other repositories and publish local history by "pushing" branches to other repositories. You see what others have contributed by "pulling" branches into your local repository.

7. Go back to your local terminal window and send your committed changes to Bitbucket using git push origin main. This command specifies that you are pushing to the main branch (the branch on Bitbucket) on origin (the Bitbucket server).

You should see something similar to the following response:

 $ git push origin main 
 Counting objects: 3, done.
 Writing objects: 100% (3/3), 253 bytes | 0 bytes/s, done.
 Total 3 (delta 0), reused 0 (delta 0) To https://emmap1@bitbucket.org/emmap1/bitbucketstationlocations.git
  * [new branch] main -> main
 Branch main set up to track remote branch main from origin.

Your commits are now on the remote repository (origin).
Local system to Bitbucket server "Origin"

8. Go to your BitbucketStationLocations repository on Bitbucket.

9. If you click Commits in the sidebar, you'll see a single commit on your repository. Bitbucket combines all the things you just did into that commit and shows it to you. You can see that the Author column shows the value you used when you configured the Git global file ( ~/.gitconfig).
If you click Source in the sidebar, you'll see that you have a single source file in your repository, the locations.txt file you just added.
Git commit source in Bitbucket

Remember how the repository looked when you first created it? It probably looks a bit different now.

