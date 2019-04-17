# Langley Foxall Git Workflow

Deriving from [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow), we 
have decided on the best route forward for how we should work with git.

## Branches
Branches should be harmonious between projects and follow a set standard. Branch setup should be completed
after the initial commit, with the correct protection rules in place.

* `master` should be the working development branch [UNSTABLE]
* `feature/*` branches created from master for each feature, change or fix
* `hotfix/*` branches should only be created off of `staging` or `production` and merged accordingly, this is only for fixes directly in `production` or `staging`, for other fixes use `feature/*` branches
* `staging` should contain the latest, customer visible changes and be on the `Workshop`
* `production` should contain stable code on live servers.

#### Open Source
Open source projects should always be forked, rather than branched in the same repo. This ensures that the
original repository is a reviewed and clean set of lots of contributions.

#### Branch Protection
`master` and `production` should require pull requests to push code to. 

The `master` branch should be reviewed by at least a development peer, and any code going to `production`
should be reviewed by at least `2` people, with one of those being a Senior/Lead Developer.

#### Feature Branches
Feature branches are intended to hold code away from the `master` branch whilst in development, in order to
keep the `master` branch functional (for the most part) and complete at all times.

Once a feature has been completed and tested, a Pull Request should be created to merge that feature into 
the `master` branch. This allows for another team member to sanity check the code and for Travis CI to run 
any tests/linting.

In the case that the project is a solo project, an external reviewer should be requested. This should be a
Senior/Lead Developer.

## Pull Requests
Reviewers should keep commerciality in mind, and only pull up infringements of the coding standards, security
issues or efficiency issues.

Reviewers must directly link to the relevant section of the documentation when reviewing - refraining from
re-wording the documentation in their own words.

Only the person who created the pull request or admin should merge it. 
Even though it may of been accepted by the reviewers the person who created it might of noticed a change after the fact or admins might have a reason for delaying the merge.

Developers should avoid bulk changing indentation or spacing, as this can make pull requests more
difficult to review. It these kind of bulk changes are required, they should ideally be submitted
as a separate, independent pull request.

## Commits

#### Frequency
* Commits should be made after every task is completed. 
* Commits should NEVER be more than a day apart.

#### Messages
Commit messages should be:
* Descriptive
* Commands (Add, not Added. Fix, not Fixed.)
