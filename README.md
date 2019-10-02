# git_rebase

Using git rebase, we can merge files by re-writing the commit history in order to produce a straight, linear succession of commits.

In this example or test, we have 3 branches: master, add-echo & add-reverse.

To resolve the merge conflict using rebase, I have created a file (master.txt) that has some unique content for each of the 3 branches.

`@master: master.txt`
`test:master`

`@add-echo: master.txt`
`test:add-echo`

`@add-reverse: master.txt`
`test:add-reverse`

After, committing & pushing the files & content to their respective branches, we would use `git rebase` to bring the commits on branches: `add-echo` & `add-reverse` to `master` 

The below steps specify or describe the commands that would be executed to achieve this task.

## Steps 


### 1. Create master.txt file in all the branches with unique content
```
1. git checkout master
2. (Create file master.txt & add content: "test:master")
3. git add .
4. git commit -m "@master: change content in master.txt file"
5. git push origin master
```

Repeat the above steps for other 2 branches: `add-echo` & `add-reverse`

### 2. Use git rebase to bring all the commits of branch `add-echo`

```
1. git checkout add-echo
2. git rebase master
```

Post this command, we would get a merge conflict error. This happens because, we are trying to change the same file & line of code in `add-echo` & `master` branch. We can manually resolve this error & proceed with below steps.

```
3. git add .
4. git rebase --continue
5. git checkout master
6. git merge add-echo --ff (Forcefully merge the content of the files)
7. git push origin master
```

Post these commands, all the commits that happen in the branch `add-echo` gets integrated to `master`. Any merge conflicts can be resolved manually, forcefully or via editor.

### 3. Use git rebase to bring all the commits of branch `add-reverse`

```
1. git checkout add-reverse
2. git rebase master
```

Post this command, we would get a merge conflict error. This happens because, we are trying to change the same file & line of code in `add-reverse` & `master` branch. We can manually resolve this error & proceed with below steps.

```
3. git add .
4. git rebase --continue
5. git checkout master
6. git merge add-echo --ff (Forcefully merge the content of the files)
7. git push origin master
```

Post these commands, all the commits that happen in the branch `add-reverse` gets integrated to `master`. Any merge conflicts can be resolved manually, forcefully or via editor.

