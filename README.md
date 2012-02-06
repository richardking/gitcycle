Gitcycle
========

Tame your development cycle.

Gitcycle is a drop-in replacement for git that makes pull request dev cycles super easy.

Get Started
-----------

Visit [gitcycle.com](http://gitcycle.com) to set up your environment.

Create Branch
-------------

Checkout the branch that you will eventually merge your feature into:

	gitc checkout master

Type `gitc` + your ticket URL to create a new branch:

	gitc https://xxx.lighthouseapp.com/projects/0000/tickets/0000-my-ticket

Pull Changes from Upstream
--------------------------

When you're developing, you may need to pull new changes from an upstream branch:

	gitc pull

Commit Code
-----------

Commit all changes and open commit message in EDITOR with ticket info prefilled:

	gitc commit

Push Changes
------------

	gitc push

Discuss Code
------------

After pushing one or two commits, put the code up for discussion:

	gitc discuss

Mark as Ready
-------------

When the branch is ready for merging, mark it as ready:

	gitc ready

This will mark the pull request as "Pending Review".

Code Review
-----------

Managers will periodically check for "Pending Review" issues on GitHub.

Once reviewed, they will mark the issue as reviewed:

	gitc reviewed [GITHUB ISSUE #] [...]

Quality Assurance
-----------------

QA engineers will periodically check for "Pending QA" issues on Github.

To create a new QA branch:

	gitc qa [GITHUB ISSUE #] [...]

This will create a new QA branch containing the commits from the related Github issue numbers.

This branch can be deployed to a staging environment for QA.

QA Fail
-------

If a feature does not pass QA:

	gitc qa fail [GITHUB ISSUE #] [...]

To fail all issues:

	gitc qa fail

This will add a "fail" label to the issue.

QA Pass
------- 

If a feature passes QA:

	gitc qa pass [GITHUB ISSUE #] [...]

To pass all issues:

	gitc qa pass

This will add a "pass" label to the issue and will complete the pull request by merging the feature branch into the target branch.

More
----

### Checkout Upstream Branch

If you are working in a fork, it is easy to checkout upstream branches:

	gitc checkout [BRANCH]

### Collaborate

Its easy to checkout branches from other forks:

	gitc checkout [USER] [BRANCH]

### QA Status

See who is QA'ing what:

	gitc qa

### Redo Branch

If you associate the wrong branch with a ticket, use `gitc redo` to fix it.

Checkout the branch that you will eventually merge your feature into:

	gitc checkout master

Type `gitc redo` + your ticket URL to reset the branch:

	gitc redo https://xxx.lighthouseapp.com/projects/0000/tickets/0000-my-ticket

Todo
----

* Add ability to associate multiple branches/pull requests with one Lighthouse ticket
* Add comment on lighthouse with issue URL
* gitc discuss should tag issue with 'Discuss'
* On pass or fail, send email to Github email
* Note you can use gitc with a string
* gitc qa pass, should not set ticket to pending-approval if its already resolved
* If gitc reset happens on branch with Github issue, close the existing issue
* Add comment on lighthouse with issue URL
* Instead of detecting CONFLICT, use error status $? != 0
* Label issues with ticket milestone
* gitc qa pass # since we're changing this to pass all the tickets, we need to loop through all the merged issues and update the lighthouse state to pending-qa
* There's still a Tagging Issue I tried to fix parseLabel http://d.pr/8eOS , Pass should remove Pending, but remove the Branch Name
* gitc ready - possibly do syntax checks