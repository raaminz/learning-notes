### How to run gofumpt on changes before git commit only on .go files?


To run `gofumpt` on changes before git commit only on .go files, you can use a pre-commit git hook. First, you must have `gofumpt` installed. If it's not, install it with this command: `go get -u mvdan.cc/gofumpt`.

Here are the steps:

1. Navigate to the `.git/hooks` directory in your Git repository.

2. Create a file `pre-commit` if it doesn't exist already, and make it executable with `chmod +x pre-commit`.

3. Open the `pre-commit` file in a text editor and add the following script:

```bash
#!/bin/sh

STAGED_GO_FILES=$(git diff --cached --name-only -- '*.go')

# If there's no .go files in staging, exit
if [[ "$STAGED_GO_FILES" = "" ]]; then
  exit 0
fi

# Run gofumpt on each file
for FILE in $STAGED_GO_FILES; do
  gofumpt -w $FILE
  git add $FILE
done

exit 0
```

Now `gofumpt` will be run on every staged .go file whenever you commit. The `-w` option is used to write result to file instead of stdout.

Remember that this hook won't be shared when your repository is cloned or pulled by others, as Git doesn't include the `.git/hooks` folder in the distributed code. You might want to include a setup script to create the hook, or use a Git hooks manager like `pre-commit` (https://pre-commit.com).


### How to have add a git hook file globally?

To setup a git hook globally, follow these steps:

1. Create a directory for your global hooks:
   ```
   mkdir ~/.git-hooks
   ```

2. Create a hook in this directory. For example, a pre-commit hook:
   ```
   touch ~/.git-hooks/pre-commit
   ```
   Don't forget to make your hook script executable:
   ```
   chmod +x ~/.git-hooks/pre-commit
   ```
   Then, add your desired bash script in the `pre-commit` file.

3. Set the `core.hooksPath` to your global hooks directory:
   ```
   git config --global core.hooksPath ~/.git-hooks
   ```

Now, the hooks in this directory will be used for all repositories you use on this machine. Remember that the hooks are local to the machine, and are not part of the git repository, so they will not be pushed to the remote repository.
