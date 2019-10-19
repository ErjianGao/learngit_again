git reflog:record every commit id
git diff [filename]:show the changee of the file
git diff HEAD -- [filename]:show the difference between the current file and the latest file in the repository 
git reflog:record every commond
git reset --hard [commit id]:recover the old version, furthermore, the HEAD^ means the last version, and the HEAD means the current version
git reset HEAD [filename]:get the change in stage back to the workplace
cat file:show the content of file
git log: show the history of the commit of version repository
git init:initialize empty Git repository
git add [filename]:add the file to the stage
git commit -m [comments]:add the files in stoge to the repository
git status:check the status of the present repository
git checkout -- file:discard all the change of the files in the workplace, which means the file will return to the last "git commit(or add)" status
git remote add origin git@github.com:username/[remote repository name].git:associate a existing repository with the remote repository, and the name of the remote repository is "origin", and this is the git default name
git push -u origin master:push the current branch master to the remote, and the -u ref means that git will not only push the master branch to the new master branch but also associate the local master branch with the local master branch, which means it will simplify the command when pull and push content


why the Github need the SSH Key? Because GitHub needs to recognize the commit you pushed is exactly you pushed, and not a fake, and Git support the SSH protocal.So if Github knows your public key, it can confirm that only you can push the commit.


problem:
1.I initialized a git repository locally, putting some files in it and did some add and commit operations. 
2.Then I created a remote repository and a README file in the github. 
3.I add the git repository as remote repository in local repository, named "origin"
	git remote add origin git@github.com:ErjianGao/learngit_again.git
4.But when the local repo want to synchronize the remote repo to local repo, and prepare for pushing the local repo to the remote, the git report an error
	fatal: refusing to merge unrelated histories
solution:
The reason why this happen is that the local repo and the remote repo are actually two repos. If I directly clone the remote to the local, there won't be any questions. 
And by looking for the Internet, it can be solved by using option "--allow-unrelated-history"(this option can merge two repos which were independently started)
	$git pull origin master --allow-unrelated-histories
The above is to pull the files from the remote repo to the local repo
And the next is to push the local commit to the remote github repo, using the following command.
	git push <remote host name> <local branch name>:<remote branch name>


pull
git pull command is basically the conbination of "git fetch" and "git fetch" command, Git fetch content from the appointed repos, and immidiately try to merge to your branch, which makes it an easier and more comfortable work flow.

The solution of this question mainly refers the blog from this website:https://blog.csdn.net/w88193363/article/details/80593429
