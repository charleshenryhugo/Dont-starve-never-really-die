# Introduction

In game `Don't starve`, the save-files get deleted if the player dies. This is quite annoying if, for example, you have survived for 100 days and suddenly get killed by a tentacle.

Most solutions for this issue focus on backup files. Namely, backup files when you are still alive and recover them if you die. I tried these solutions for a while and finally `git` came to my mind.

## save-files

We need to find save-files directory first. On MacOS, for example, they may be located at

`~/Library/Application Support/Steam/userdata/<your-id>/219740/remote/`

( `219740` is the id of `Don't starve` )

`ls` the save-files directory, you will see several executable files including `profile`, `saveindex`, `morgue`. They are the save-files we've been looking for.

## Solution

There's no need to figure out what roles these files are playing. Just backup and recover them with `git`.

```
cd ~/Library/Application Support/Steam/userdata/<your-id>/219740/remote/
git init
```

backup ( == commit everything you've done ):

```
git add .
git commit "your message"
```

recover the most recent archive if you are killed ( == Discard all changes since the last commit ):

```
git checkout ./
```

There're much more you can do if you are familiar with `git`.

## Author

ZHU YUE