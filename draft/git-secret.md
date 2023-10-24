Do you know, you can use "git-secrets" tool to sniff out secrets and prevent commits before pushing secrets to the repo?

It's an open-source git-secrets tool from AWS Labs to scan Git source repositories and find code that might potentially include sensitive information, such as user passwords or AWS access keys, or that has any other security issues.

git-secrets scans commits, commit messages, and merges to prevent sensitive information such as secrets from being added to your Git repositories.
For example, if a commit, commit message, or any commit in a merge history matches one of your configured, prohibited regular expression patterns, the commit is rejected.

Always remember: "Prevention is better than cure!"