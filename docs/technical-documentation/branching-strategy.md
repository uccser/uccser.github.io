# Branching Strategy

We use Vincent Driessen's [git-flow branching model](http://nvie.com/posts/a-successful-git-branching-model/) for managing development.
Please read this article to understand our branching methods, and how to perform clear branches and merges.

Our projects are released with explicit versioning (compared to continous delivery of modern web apps), and the `git-flow` branching model has proven very successful for us.

Specifically for our main repositories:

- There is a `master` branch for production releases.
- There is a `develop` branch for the latest stable development version.
    - This can also be called the staging environment or just 'staging'.
    - This means anything in the `develop` branch should be ready for release.
- The default branch on GitHub for our repositories is the `develop` branch.
- We create new branches off the `develop` branch.
- We create a new branch for each task of work, no matter how small it is.
    - For example: If the work was solving issue 117 in a repository, the new branch could be named `issue/117`.
- When a branch is completed, a pull request is created on GitHub for review.
- Branches are merged back into `develop`.

Our smaller non-critical repositories (for example, this documentation repository), may only have one branch.
