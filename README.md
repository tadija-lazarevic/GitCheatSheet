CheatSheat for GIT

**Create - from existing data**

	cd ~/my_project_directory
	git init
	git add . 


**Create - from existing directory**

	git clone ~/existing_repo ~/new/repo
	git clone git://host.org/project.git
	git clone ssh://user@host.org/project.git



**Clone**

	git clone [url]                                      #klonira ceo projekat, pulluje najnoviju verziju
	git clone [url] myFolder                             #klonira ceo projekat u myFolder
	git pull                                             #radi isto sto i git fetch&&git pull - ali u jednoj komandi - sinhronizuje lokalni sa originom
 

**Add**

	git add -u                                           #dodaje samo modifikovane fajlove
	git add .                                            #dodaje sve fajlove
 

**Remote**

	git clone -o [origin_name]                         #menja default remote name(origin) u [origin_name] --retko se menja
	git remote show origin                             #prikazuje sve remote branch-ove


**Fetch**

	git fetch origin                                   #sinhronizuje moj master branch sa live verzijom
	git fetch                                          #sinhronizuje promene mog lokalong repo sa live verzijom
	git pull                                           #povlaci sve promene sa origin repo-a
	git pull origin/[branch_name]                      #povlaci sve promene sa remote branch-a


**Branching**

	git branch                                         #pokazuje trenutni branch
	git branch -v                                      #pokazuje zadnji komit na trenutnom branchu     
	git branch --all                                   #izlistava sve branch-ove (lokalno i na serveru)
	git checkout -b [branch_name]                 	   #pravi novi branch i menja trenutni branch u napravljeni
	git push origin [branch_name]                  	   #push-uje lokalni branch na origin remote server
	git push origin --delete [branch_name]    		   #brise branch sa remote servera
	git branch -d [branch_name]                        #brise branch lokalno
	git branch --merged                                #pokazuje branch-ove koji su merged
	git branch --no-merged                             #pokazuje branch-ove koji jos nisu merged

**Merging**

	git merge [branch_name]                            #merge-ujem [branch_name] sa masterom
	git diff master [branch_name]                      #proverim da li postoje razlike (ne bi trebalo)


**Conflict**

	git status                                         #izlistava fajlove koji nisu merged
	git reset --hard                                   #brise staged i promene u direktorijumu
	git clean -f -d                                    #brise untracked fajlove
	git log                                            #poslednji komitovi u lokalnom repozitorijumu


**Undo**

	git reset HEAD [file_name]                         #diskarduje komit ali promene u fajlu i dalje ostaju
	git checkout -- [file_name]                        #diskarduje promene u fajlu lokalnog repozitorijuma
	git reset --hard HEAD                              #diskarduje promene svih fajlova
	git revert b53b3c796b6fdd3e7a02ef06a2e1035db743c137         #revert komit - vraca komit koji je greskom otisao


**Diff**

	git diff master master/origin                      #razlike izmedju lokalnog mastera i origin mastera
	git log --graph  --decorate                        #ispisuje log komitova
	git diff [branch_name] [branch_name]               #razlike izmedju dva branch-a
	git diff --name-only  [branch_name] [branch_name]  #pokazuje samo izmenjene fajlove
	git diff [local_branch] [origin/remote_branch]     #razlika izmedju lokalnog i remote branch-a
	git log --oneline fixing_bugs_23-05-2015 ^master   #razlika komitova izmedju dva branch-a
	git log --oneline fixing_bugs_23-05-2015..master   #isto sto i iznad
	git diff -R                                        #diff reversed


**Stash**

	git stash                                          #sacuva sve izmene i vraca u najnoviju komitovanu verziju
	git stash save "Poruka"                            #isto sto i ovo gore samo sa deskriptivnom porukom
	git stash list                                     #lista sve stash 
	git stash apply stash@{0}                          #vraca odredjeni stash
	git stash drop stash@{0}                           #brise odredjeni stash, kad ni jedan nije zadat brise zadnji      


**Tags**

	git tag Release-0.0.1 -m "Release of Software on May 22"                #dodaje tag koji oznacava verziju software-a
	git push origin Release-0.0.1                                           #pushuje odredjeni tag na origin remote


**Status**

	git status -uno                                     #ne prikazuje untracked fajlove (git status --untracked-files=no)


