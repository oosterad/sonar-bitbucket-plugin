# sonar-bitbucket-plugin
Branch of the original sonar bitbucket plugin

After testing, I encountered a bug. The bug occurs when the following is done:

* a sonar issue is found on a line, a new comment is added to the PR
* the sonar issue fixed, the comment is deleted, which result in a delete flag set to true in the comment
* a new sonar issue is introduced on the same line, the plugin tries to update the deleted comment, which is not allowed and results in an error from Bitbucket

This is fixed by ignoring all deleted comments when search for a comment on the same line. So instead of updating, a new comment will now be created.
