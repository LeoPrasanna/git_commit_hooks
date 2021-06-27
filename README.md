# git_commit_hooks
# prepare-commit-msg

This hook is invoked by git-commit[1] right after preparing the default log message, and before the editor is started.

It takes one to three parameters. The first is the name of the file that contains the commit log message. The second is the source of the commit message, and can be: message (if a -m or -F option was given); template (if a -t option was given or the configuration option commit.template is set); merge (if the commit is a merge or a .git/MERGE_MSG file exists); squash (if a .git/SQUASH_MSG file exists); or commit, followed by a commit object name (if a -c, -C or --amend option was given).

If the exit status is non-zero, git commit will abort.

The purpose of the hook is to edit the message file in place, and it is not suppressed by the --no-verify option. A non-zero exit means a failure of the hook and aborts the commit. It should not be used as replacement for pre-commit hook.

The sample prepare-commit-msg hook that comes with Git removes the help message found in the commented portion of the commit template.

# commit-msg
 This hook is invoked by git-commit[1] and git-merge[1], and can be bypassed with the --no-verify option. It takes a single parameter, the name of the file that holds the proposed commit log message. Exiting with a non-zero status causes the command to abort.

The hook is allowed to edit the message file in place, and can be used to normalize the message into some project standard format. It can also be used to refuse the commit after inspecting the message file.

The default commit-msg hook, when enabled, detects duplicate Signed-off-by trailers, and aborts the commit if one is found.