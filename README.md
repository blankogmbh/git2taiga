# Webhook to close Taiga.io issues with GitLab commits

The script enables you to use the [GitLab closing pattern](http://doc.gitlab.com/ee/customization/issue_closing.html) to close issues, tasks and userstories in your [Taiga.io](https://taiga.io) project.

## Installation
Copy this folder to some PHP (>=5.3) supporting Webserver which is accessable by your GitLab instance.

### Copy and change configuration
1. copy config.default.php to config.php
2. update config.php with your settings

### Set up your project in GitLab
In the following steps, please replace `PROJECT_NAME` with yout Taiga project URL and `http://example.com/git2taiga/` with the URL of this script.

1. Add a new web hook for “Push events” to your project with the target url `http://example.com/git2taiga/?project=PROJECT_NAME`
2. (optional) To link issues in GitLab to your Taiga installation add a custom issue tracker in project services using the following urls:<br>
	*Project url:* http://example.com/git2taiga/?redirect&project=PROJECT_NAME<br>
	*Issues url:* http://example.com/git2taiga/?redirect&project=PROJECT_NAME&issue=:id<br>
	*New issue url:* http://example.com/git2taiga/?redirect&project=PROJECT_NAME&issue=new<br>

### Closing issues, user stories or tasks

When a commit is merged into the master and uses the [GitLab closing pattern](http://doc.gitlab.com/ee/customization/issue_closing.html) the task is set to the first status that is marked as closed in the Taiga settings. A comment linking to the GitLab commit will be add to the item.

When the current status of the item is higher then the first close status this script will not change anything.