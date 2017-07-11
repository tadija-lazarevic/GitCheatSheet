**CheatSheat for GIT**



**Config - setup git**

	git config --global user.name "Username"
	git config --global user.email "some@email.com"
	

**Create - from existing data**

	cd ~/my_project_directory
	git init
	git add . 



**Clone**

	git clone ~/existing_repo ~/new/repo
	git clone git://host.org/project.git
	git clone ssh://user@host.org/project.git
	
	git clone [url]                                      #klonira ceo projekat, pulluje najnoviju verziju u folder tog projekta (stoji na kraju url-a)
	git clone [url] myFolder                             #klonira ceo projekat u myFolder
	
 	

**Add**

	git add .                                            #dodaje sve fajlove
 	git add -v 										     #verbose
 	git add . -u 										 #dodaj sve izmenjene fajlove sem untrekovanih


**Fetch && Pull**

	git fetch                                          #povlaci sve brencheve i/ili tagove (zajedno cine "refs"), apdejtuje sve trekovane brencheve
	git pull                                           #povlaci sve izmene sa remote repozitorijuma u moj trenutni brench
	git pull origin/[brench_name]                      #povlaci sve izmene sa remote brencha u odredjeni lokalni brench



**brenching**

	git remote show origin                             #lista sve remote brencheve
	git checkout -b [brench_name]					   #pravi novi brench i prelazi u taj brench
	git brench                                         #pokazuje trenutni brench
	git brench -v                                      #pokazuje zadnji komit na trenutnom brenchu     
	git brench --all                                   #lista sve brench-ove (lokalno i remote)
	git push origin [brench_name]                  	   #pushuje lokalni brench na origin remote server
	git push origin --delete [brench_name]    		   #brise brench sa remote servera
	git brench -d [brench_name]                        #brise brench lokalno
	git brench --merged                                #pokazuje brench-ove koji su merged
	git brench --no-merged                             #pokazuje brench-ove koji jos nisu merged
	git remote update origin --prune                   #update-uje branch listu i remote i lokalno

**Merging**

	git checkout master 							   #prelazim u master brench
	git merge [brench_name]                            #merge-ujem [brench_name] sa masterom
	git merge origin/development					   #merge-uje devel sa masterom

**Status**


	git status                                         #lista fajlove koji nisu merged
	git status -uno                                    #ne prikazuje untracked fajlove (git status --untracked-files=no)
	git log                                            #lista komitova
	git ls-files . 									   #lista sve fajlove u repou
	git ls-files . --ignored --exclude-standard --others	#lista git-ignored fajlove
	git ls-files . --exclude-standard --others		   #lista untrekovane fajlove
	git clean -fd                                      #brise untracked fajlove


**Undo**

	git reset										   #undo posle git add .
	git reset --soft HEAD^							   #undo posle git commit -m 'update'
	git reset HEAD [file_name]                         #undo posle git add [file_name] - undo posle dodavanja jednog fajla
	git checkout -- [file_name]                        #diskarduje izmene u jednom fajlu 
	git checkout -- . 								   #diskarduje izmene u svim fajlovima
	git revert b53b3c796b6fdd3e7a02e		           #revert komit - vraca komit koji je greskom otisao (list svih komitova git log)


**Diff**

	git diff --name-only --diff-filter=U 			   #lista sve fajlove koji imaju konflikte posle stash-a
	git diff master master/origin                      #razlike izmedju lokalnog mastera i origin mastera
	git log --graph  --decorate                        #graph brenchova i komitova
	git diff [brench_name] [brench_name]               #razlike izmedju dva brencha
	git diff --name-only  [brench_name] [brench_name]  #razlike izmedju dva brencha samo fajlovi
	git diff [local_brench] [origin/remote_brench]     #razlika izmedju lokalnog i remote brench-a
	git log --oneline [brench_name] ^master   		   #razlika komitova izmedju dva brench-a
	git log --oneline [brench_name]..master            #isto sto i iznad
	git diff -R                                        #diff reverzno
    

**Stash**

	git stash                                          #sacuva sve izmene i vraca u najnoviju komitovanu verziju
	git stash save "Poruka"                            #isto sto i ovo gore samo sa deskriptivnom porukom
	git stash list                                     #lista sve stash 
	git stash apply stash@{0}                          #vraca stash@{0}
	git stash drop stash@{0}                           #brise odredjeni stash, (kad ni jedan nije zadat brise zadnji)
	git stash show -p stash@{0}						   #prikazuje sta je u stash-u
    git diff stash@{0}  							   #razlike u stashu


**gitignore**											#dodavanje gitignore fajla posle komita

	git rm -r --cached .
	git add .
	git commit -m ".gitignore is now working"


**Remove files from repo**

	git rm --cached [file_name]						   #brise fajl iz repozitorijuma, ne i fizicki
	git rm --cached -r [dir_name]					   #brise direktorijum iz repozitorijuma, ne i fizicki


**Tags**

	git tag Release-0.0.1 -m "Release of Software on May 22"                #dodaje odredjeni tag 
	git push origin Release-0.0.1                                           #pushuje odredjeni tag na origin remote

