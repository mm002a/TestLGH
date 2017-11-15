# TestLFS
### This is just to see how LFS support works.
_On GitHub_  
Sorted ssh authentication :-)

Sorted gpg signing ;-)

Some progress this works on GitHub! Now For GitLab!!  
OK So this is how it works:  
'git lfs install'  
Choose the (potentially) big files (or file types) and 
add them to the .gitattributes file.  
`git lfs track "*.deb"`  
Add `.gitattribites` to your repo!  
Use:
`$ git lfs migrate info --above=<size>` to find big files.  
`$ git lfs migrate import INCLUDE and EXCLUDE`  
to change the history 
to big files or on the server, small files are in the repo.

`$ git lfs {track,ls-files,env}` are useful info commands.  
This seems a good source of info: https://github.com/git-lfs/git-lfs/wiki/Tutorial  

If you (accidentally!) transfer a file to the lfs server you can recover it  
by:  
`$ git lfs {pull,checkout,fetch -- {filename}}`   
especially: `git lfs pull` (generates an error message!?!?) (works without the network -> local recovery)

_On GitLab (at Daresbury)_

There appears to be a problem.  
I copied the repo to a new folder and deleted `.git/`  
I then did a `git init` and pushed to `GitLab`  
*this worked* (no `lfs files`)  
I then added an `lfs` file (with `.gitattributes`)

 I receive this output:  
 `Remote "origin" does not support the LFS locking API. Consider disabling it with:
   $ git config lfs.https://gitlab/cct65/TestLFSGitLab.git/info/lfs.locksverify false
     Post http://hcp004.hartree.stfc.ac.uk/cct65/TestLFSGitLab.git/info/lfs/locks/verify: dial tcp 193.62.122.5:80: 
     i/o timeout error: failed to push some refs to 'git@gitlab:cct65/TestLFSGitLab.git'`
 
 When I set `locksverify false` the push just hangs :-(
 
 Next - repeat to verify procedure!
