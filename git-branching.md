## Overview
As we build out the DevOps Platform we would like to employ a standard Git branching strategy across our product development teams. This will be beneficial for achieving standards compliance, onboarding and reporting, and will help to remove uncertainty in the branching process.
## Gitflow
We have chosen to use [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/) as our current branching strategy. Though perhaps not the best choice for true Continuous Delivery pipelines, Gitflow does provide a controlled branching model with some built-in safety nets that are likely to aid us as we progress to more mature pipelines. It is also well documented, with plenty of resources available online.

### COMPANY's Gitflow interpretation
While the above documentation represents a reasonable guide to Gitflow, we have added the following modifications for use within our org:
- Our 'main' branch is called _main_ rather than _master_
- Where relevant, release branches do not have to be removed following merge to main and develop, and may be retained for as long as is necessary
- In general, **merge requests will be used within GitLab rather than the merge commands given in the linked guide**. There is an exception to this however - when merging any branch to main, a fast-forward merge should be performed. GitLab does not allow mixing of merge methods, meaning this merge should be carried out from the command line using, e.g:
    - _git switch main_
    - _git merge --ff-only release-2.1.3_
    - _git push_

### Branch Protection
Our workflow requires the use of _protected branches_. In general, protected branches cannot be directly pushed to; changes must come via merge request. (This is accomplished by setting 'Allowed to push' to 'No one'). There may be differences between projects, but at the very least _develop_ and _main_ branches must be protected.   

Protected branch configuration can be found under _Repository Settings >> Protected branches_ in your project's settings.
In the image below, only project maintainers are allowed to merge to these branches, while three named users have been given the ability to push to main. This allows fast-forwarding the main branch as described above. 

![Branch Protection](/img/branch-protection.png)
## Going Forward
As our DevOps maturity grows we may find that we would be better served by a different branching strategy. We will review our needs periodically and collaborate with the Product Development teams to ensure we are following processes that help us to deliver.
## JIRA Integration
GitLab features some useful, straightforward integration with JIRA. Branches and merge requests can be created directly from a JIRA issue, and including a JIRA issue ID in a branch name, merge request or commit message will link that item with the issue.
