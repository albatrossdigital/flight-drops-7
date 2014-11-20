# How to Update Flight based repos

### First update 

```
git pull origin master
```

**NOTE:** might need to call `git pull github master` and `git pull pantheon master` seperately.


### Checkout new branch

```
git checkout -b updating-flight
```


### Pull down latest flight

```
git pull -s recursive -X theirs git@github.com:albatrossdigital/flight-drops-7.git
```


### Resolve any merge conflicts

```
git mergetool
```


**NOTE:** You may be prompted to choose between {local} and {remote} files just choose "m - modified" if it corresponds to the remote files you may also be forced to click through a bunch of files on the command line.  Because you've chosen "theirs" no action will actually be necessary.

**Once merged, you can remote any "orig", ect files.**

### shows them 

```
git status -su | grep -e"\.orig$" | cut -f2 -d" "
```


### Deletes them

```
git status -su | grep -e"\.orig$" | cut -f2 -d" " | xargs rm -r
```

### Commit changes

```
git commit -m "Updating to flight 7.xx"
```


### Checkout master, merge, push

```
git checkout master
git merge updating-flight
git push origin master
```
