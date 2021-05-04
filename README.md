# REF 
https://stackoverflow.com/questions/62785290/installing-previous-versions-of-a-formula-with-brew-extract
https://stackoverflow.com/questions/39187812/homebrew-how-to-install-older-versions/46306176#46306176

By rjollos, https://stackoverflow.com/users/121694/rjollos

Create [homebrew-repo] on GitHub, then added the tap, then initialized the tap using tap-new.

# Steps

```
$ TAP=jason202005/homebrew-repo
$ TAP_PATH=$(brew --repository)/Library/Taps/$TAP

$ brew tap $TAP
==> Tapping rjollos/repo
Cloning into '/usr/local/Homebrew/Library/Taps/jason202005/homebrew-repo'...
warning: You appear to have cloned an empty repository.
Tapped (16 files, 22.2KB).

$ brew tap-new $TAP
==> Created jason202005/repo
/usr/local/Homebrew/Library/Taps/jason202005/homebrew-repo

$ cd $TAP_PATH

$ git add .

$ git commit -m "Initialized with template files"
[master (root-commit) c7c4bed] Initialized with template files
 2 files changed, 29 insertions(+)
 create mode 100644 .github/workflows/main.yml
 create mode 100644 README.md

$ git remote -v
origin  https://github.com/jason202005/homebrew-repo (fetch)
origin  https://github.com/jason202005/homebrew-repo (push)
```

# Extract the versioned formula:
```
$ brew extract --version 1.2.1 hodoop $TAP
==> Searching repository history
==> Writing formula for hadoop from revision 11dfa2d to:
/usr/local/Homebrew/Library/Taps/jason202005/homebrew-repo/Formula/hadoop@1.2.1.rb
```

# Add the formula:

```
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 753 bytes | 753.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/jason202005/homebrew-repo
 * [new branch]      master -> master
```
