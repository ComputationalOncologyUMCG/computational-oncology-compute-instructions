Overview
========

.. _github_teams_and_repos:
GitHub teams and repositories
-----------------------------

Code in our group is organized via GitHub. Projects are organized in repositories and teams. Generally, a project will have a team assigned to it, with a single repository that is named the same as the team. Users are then made members of that team, so that they can make edits on that repository.

Sometimes projects contain multiple work packages or projects, or a project is too big to put into a singular github repository. In these cases the single-repo-single-team principle still holds true. The way this is managed, is by making subteams inside parent teams.

For example let us say that we are developing ToolX for use on both python and R. We would then create a parent Team called ToolX. This team would then have two subteams called ToolX-py and ToolX-R, each with their own repository.

To start developing using the group github, make sure you have an account and proper access. See :doc:`prerequisites`


.. _proper_github_usage:
Proper GitHub usage
-----------------------------

Many projects do not think about github and code sharing until the very last moment, where they simply upload all the code all in one go. While this generally works, it is not the most efficient, traceable and collaborative approach.

Ideally, you start out with a GitHub repository, and keep adding to it as the project progresses. This allows you to trace where you did what, and if you break anything, allows you to trace back where you might have broken it. It also allows collaborators to look at your code, to either work on it themselves, or to use it as an inspiration. It also makes it easier for you to switch between by machines, by just pushing and pulling changes across your machines.
Some advanced options also include generating images containing your code, allowing you to share pipelines and tools.

Git and Github can be used via the command line, but a lot of users prefer a graphical interface. Here there are two applications documented :doc:`github_via_sourcetree` and :doc:`github_via_github_desktop`


.. _using_gitlab_planning:
Planning via GitLab
-----------------------------

You can in addition to using GitHub for your code, also use GitLab (not the same), to plan your projects. You can request one of the admins to add you to the group on GitLab, and ask them to set it up so that GitLab will show your GitHub code. See :doc:`prerequisites`