## DevOps Knowledge Base

This page will host all the questions and their resolutions that were addressed for the course.

## Resolved Issues
```markdown
Master branch protection ? 
It depends on the organization for smaller companies the master branch will not be protected but for larger organizations with multiple release branches it will be controlled by build teams who might lock the branch and release it as necessary.
```

```markdown
~/.m2 repository already existed ? 
Not entirely sure why you want to do this since it is just a repo, but you can provide a separate maven repository but that will be a global change.

1) Navigate to Maven Home: eg../usr/local/maven/conf 
2) Update the settings.xml where there is definition for local repository.

Note that the above change is global and you can change it back as you need. Typically you can make a copy of the settings.xml as original and provide a new version with the required override path.

.m2/repository is a local copy for all the dependencies that projects depend on, so things just get added to the repository and are never deleted. Even if you delete the repository folder if the projects are defined correctly when you do a build it will download all the dependencies. 

This is the sequence in which maven will resolve dependency when you do the build: maven -> local repo -> artifactory/nexus -> internet.
```

```markdown
if multiple developers are working on the same branch , how to push the changes to the develop branch or QA branch , only with one developer the releases are explained . But in real time it is more than one developer works on the same release.? 
Using GitFlow at any given time two releases can be worked on simultaneously i.e the two main branches that you would be using would be release (preparing for prod release i.e qa/staging) and develop (working on next release). if you have more than those two branches as central branches then you are not using gitflow and you are adding more complexity to your branching/deployment strategy and is a sign that you are probably doing something wrong from a DevOps model.

How can multiple developers work on develop:

dev1 - create a feature branch 1 from develop

dev2 - create a feature branch 2 from develop

dev1 - when done creates a PR (pull request) to develop and lead reviews and merges the PR to develop.

dev2 - when done ensures that he pulls from develop into is feature branch 2 and ensures that all merges are successful, runs the tests and verifies that his changes still work and submits a PR. lead reviews and merges to develop.

The same process applies to when working on release branch:

release branch assuming is ready for August release and in QA and you find bugs.

dev1 - create a feature branch 3 from release

dev2 - create a feature branch 4 from release

dev1 - when done creates a PR (pull request) to release and lead reviews and merges the PR to release.

dev2 - when done ensures that he pulls from release into is feature branch 4 and ensures that all merges are successful, runs the tests and verifies that his changes still work and submits a PR. lead reviews and merges to release.
```

### About the Course
[DevOps Course by Nand](https://www.udemy.com/devops-with-git-jenkins-artifactory-and-elk-stack) 

