![Icon](https://raw.github.com/GitTools/GitTools.Core/master/GitTools_logo.png)

GitReleaseNotes
==============

[![Join the chat at https://gitter.im/GitTools/GitReleaseNotes](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/GitTools/GitReleaseNotes?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

![License](https://img.shields.io/github/license/gittools/gittools.core.svg)
![NuGet downloads](https://img.shields.io/chocolatey/dt/gitreleasenotes.Portable.svg)
[![Chocolatey](https://img.shields.io/chocolatey/v/gitreleasenotes.svg)](https://chocolatey.org/packages/GitReleaseNotes.Portable)
[![Build status](https://ci.appveyor.com/api/projects/status/br0rijb3rgn1qb0c/branch/master?svg=true)](https://ci.appveyor.com/project/GitTools/gitreleasenotes/branch/master)

Utility which makes it really easy to generate release notes for your Git project. Works with GitHub, Jira and YouTrack. TFS Support coming soon

Have a look at the release notes in this Repo for a sample of what is generated by GitReleaseNotes

## Install

    choco install GitReleaseNotes.Portable

**NOTE:** This used to be `GitReleaseNotes`, we have moved to the proper chocolatey naming convention. We have created a dependency so it will still work, but it is something to keep in mind.

This will use [Chocolatey](http://chocolatey.org) to install GitReleaseNotes into your %path%, ready to be used for any project

## Usage
GitReleaseNotes must be run inside a git repository.

    GitReleaseNotes.exe /OutputFile ReleaseNotes.md

This will write `ReleaseNotes.md` into the root of your repo, the release notes are generated by:

 - Use the git remote to connect to your issue tracker (if possible, i.e issue tracker is GitHub)
   - Otherwise specify the issue tracker on the command line (`/IssueTracker Jira /JiraServer MyJiraServer` as well as project name, check `/?` for more info)
 - Find closed issues since the last release and generate your release notes
 - Use /allTags to generate complete release notes for all releases
 - If the release notes are already generated, GitReleaseNotes will *append* **new** closed issues to your release notes, meaning all custom edits will be retained
 - Writes out the release notes following [SemanticReleaseNotes.org](http://www.semanticreleasenotes.org/)

You can also use GitReleaseNotes to create a GitHub release, and generate the release notes automatically allowing fully automated releases including release notes generation.

If you use GitHub milestones to manage your releases [GitHubReleaseNotes](https://github.com/Particular/GitHubReleaseNotes) is a similar project.

## Versioning a release
[GitVersion](https://github.com/Particular/GitVersion) is another project which can help you generate version numbers and make following Semantic Versions easily

## Publishing a release
Initial versions of this tool allowed publishing to GitHub. This has been removed.

To easily create and publish releases, use one of the following alternatives:

- GitHub => [GithubReleaseCreator](https://github.com/dazinator/GithubReleaseCreator) or [On NuGet](https://www.nuget.org/packages/GithubReleaseCreator/)
- Jira => [JiraCli](https://github.com/CatenaLogic/JiraCli)

To use this workflow you should track the current releases release notes in the repo, then on publish just take the file contents as the description with the above tool.
