git_pivotal_tracker
===========

Inspired by [Hashrocket's blend of git and Pivotal Tracker](http://reinh.com/blog/2009/03/02/a-git-workflow-for-agile-teams.html) and [Carbon Five's article on effective git workflows](http://blog.carbonfive.com/2010/11/01/integrating-topic-branches-in-git/) and [the git-pivotal gem](https://github.com/trydionel/git-pivotal), I wanted a tool that makes the git workflow fun and simple.

Included in this is a git prepare-commit-msg hook that appends the story id in the proper format to all your commit messages so that they show up in Tracker:
[https://www.pivotaltracker.com/help/api?version=v3#github_hooks](https://www.pivotaltracker.com/help/api?version=v3#github_hooks)

Features
--------

* `git-story`
* `git-feature`
* `git-bug`
* `git-chore`

These commands collect the first available story from your Pivotal Tracker project and create a topic branch for it.

* `git-finish`

When on a topic branch, this command will fetch the latest integration branch ('master' by default), rebase your topic branch from it, merge the branch into the integration branch with no-fast-forward and push the integration branch to origin.

* `git-info`

Print out the Pivotal Tracker story information for the current topic branch

Examples
--------

* FIXME (code sample of usage)

Requirements
------------

* a github account
* a Pivotal Tracker project
* Pivotal Tracker api service hook turned on for your github project (under Admin -> Service Hooks)

Install
-------

``gem install git_pivotal_tracker``

Once installed, git pivotal needs two bits of info: your Pivotal Tracker API Token and your Pivotal Tracker project id:

``git config --global pivotal.api-token 123a456b``

The project id is best placed within your project's git config:

``git config -f .git/config pivotal.project-id 88888``

If you project's access is setup to use HTTPS:

``git config -f .git/config pivotal.use-ssl 1``

If you prefer to merge back to a branch other than master when you've finished a story, you can configure that:

``git config -f .git/config pivotal.integration-branch develop``

If you prefer to fetch and rebase from origin before merging (default is no):

``git config --global pivotal.rebase 1``

If you prefer to fast-forward your merges into the integration branch (default is --no-ff):

``git config --global pivotal.fast-forward 1``

If your Pivotal Tracker user name is different than your git user name:

``git config --global pivotal.full-name 'Ben Lindsey'``

If you would like verbose logging turned on for git commands:

``git config --global pivotal.verbose 1``

Author
------

* Ben Lindsey <ben@carbonfive.com>

Contributors
------

* [https://github.com/lyahdav](Liron Yahdav)

License
-------

(The MIT License)

Copyright (c) 2011 Ben Lindsey

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
