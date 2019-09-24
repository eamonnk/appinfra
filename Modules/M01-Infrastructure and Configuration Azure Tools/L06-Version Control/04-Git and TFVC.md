

There are many options available for source-control software:

- Git is a very popular open-source distributed model versioning tool that is available in Azure DevOps, GitHub and is generally very widely used.
- Team Foundation Version Control (TFVC) is a centralized version control system that is available in Azure DevOps. 

Azure DevOps supports both Git and TFVC.


### Git (Distributed)

*Git* is a distributed version control system. Each developer has a copy of the source repository on their development machine. Developers can commit each set of changes on their development machine, and without a network connection, perform version control operations such as history and compare. 

Branches are lightweight. When you need to switch contexts, you can create a private local branch. You can quickly switch from one branch to another to pivot among different variations of your code base. Later, you can merge, publish, or dispose of the branch.

### TFVC (centralized)

TFVC is a centralized version control system. Typically, team members have only one version of each file on their development machines. Historical data is maintained only on the server. Branches are path-based and created on the server.

TFVC has two workflow models:

-  Server workspaces. Before making changes, team members publicly check out files. Most operations require developers to be connected to the server. This system facilitates locking work flows. Other systems that work this way include [Perforce](https://www.perforce.com/) and [CVS](http://www.nongnu.org/cvs/).
-  Local workspaces. Each team member checks out a copy of the latest version of the code base, and works offline as needed. Developers check in their changes and resolve conflicts as necessary. Offline, a developer can even Diff the changes they made against the latest version, and undo those changes. Another system that works this way is [Subversion](https://subversion.apache.org/).


If you have existing TFVC repos, you can migrate them to Git repos by using the [git-tfs tool](https://github.com/git-tfs/git-tfs). The tool allows you to [migrate a TFVC repo to a Git repo](https://github.com/git-tfs/git-tfs/blob/master/doc/usecases/migrate_tfs_to_git.md) with just a few commands.

For more information on getting started with Git, see [About Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control).

For more information on TFVC, see [Use Team Foundation Version Control](https://www.visualstudio.com/en-us/docs/tfvc/overview).

To view a comparison of TFVC and Git as source-control solutions, including server capabilities, client capabilities, and integration and migration capabilities, see [Git and TFVC Capabilities](https://www.visualstudio.com/en-us/docs/tfvc/comparison-git-tfvc#git-and-tfvc-capabilities).
