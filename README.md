# Git Hook: Jira commit message

This repository houses a local git commit-msg hook that can be configured on developer workstations to ensure a Jira work item number (e.g. PROJECT-123) is included in the first line of the commit message. This ensures server-side Jira and GitHub integration can work seamlessly. 


## Installation

There are multiple different options for you to set this up. Choose one of the below sections. 


### Option 1: use the pre-commit framework per repository

This option will allow you to specify the hook as a required check for a specific repository. See [pre-commit.com](https://pre-commit.com/) for full details and usage of the framework. 

1. Install pre-commit if you don't already have it:
	```
	pip install pre-commit
	```

2. Add a `.pre-commit-config.yaml` configuration file to the root folder of your repository, with details of this repository:
	```
	repos:
	- repo: https://github.com/dalebowie/git_hook_jira_commit_msg.git
		rev: "1.0"
		hooks:
		- id: jira-commit-msg
	default_install_hook_types: [commit-msg]
	```

3. Run pre-commit for your repository:
	```
	pre-commit
	```

Note: step 4 will need to be run any time you do a fresh clone of the repository.


### Option 2: global setup via hooksPath

1. Clone this repository to your workstation:
	```
	git clone https://github.com/dalebowie/git_hook_jira_commit_msg.git
	HOOK_DIR="$(pwd)/git_hook_jira_commit_msg/hooks"
	```

2. Set the global hooks path:
	```
	git config --global core.hooksPath ${HOOK_DIR}
	```


### Option 3: per-repository setup via hooksPath

Note: this procedure needs to be repeated for each clone you perform of a repository. Local git hooks do not get pushed back to origin/upstream.

1. Clone this repository to your workstation:
	```
	git clone https://github.com/dalebowie/git_hook_jira_commit_msg.git
	HOOK_DIR="$(pwd)/git_hook_jira_commit_msg/hooks"
	```

2. Change directories into the root directory of a Git repository that you want to enable the hooks for.

3. Link in the hook files:
	```
	git config core.hooksPath ${HOOK_DIR}
	```
