
# Git Auto Commit on Mac

## Protocol

### Install `fswatch`
```bash
$ brew install fswatch
```

### Run detection
A command line here is an example.
```bash
$ cd <the root of the local git repository>
$ fswatch -0 . -l 10 -e "\\.git.*" | xargs -0 -n 1 -I{} sh -c 'git add .; git commit --author="Author automatic <author@users.noreply.github.com>" -m "auto commit changes.";'
```

### Edit anything

## Caveat

1. Don't use `git commit -am` because -a doesn't treat a new file.
1. Better to put .gitignore first to prevent exhaustive detection.
1. Better to create a branch for this auto committing because the commit history gets messy about.
1. Set a latency not to commit too sensitive changes, e.g. `-l 10`.

