# Set up integrations

To get started with GhostWriter, you'll need to connect your company's resources to the platform. This includes version control systems, project management tools, and continuous integration and deployment tools. Here's a quick overview of how to connect each type of resource:

* **Version Control Systems**: GhostWriter supports popular VCS like Git, Mercurial, and Subversion. You'll need to provide access credentials and repository URLs during the integration process.
* **Project Management Tools**: GhostWriter can integrate with Jira, Trello, Asana, and other project management tools to ensure seamless collaboration. To integrate, simply provide your API keys or OAuth tokens, along with any necessary configuration details.
* **Continuous Integration and Deployment**: Connect GhostWriter to Jenkins, GitLab CI/CD, or GitHub Actions to automate documentation updates during the development process. Configure webhooks and API access for smooth integration.

# How to Set Up an Integration Between GhostWriter and Git

This how-to guide will walk you through the process of integrating GhostWriter with your Git repository, enabling the platform to access your site's code and generate documentation based on the information found within. Follow these steps to establish a secure connection between GhostWriter and your Git repository.

## Prerequisites

1. A GhostWriter account
2. A Git repository containing your site's code

## Step 1: Generate an Access Token or SSH Key

First, you'll need to create an access token or SSH key to authenticate GhostWriter's connection to your Git repository.

### For GitHub:

1. Log in to your GitHub account.
2. Click on your profile picture in the top-right corner and select "Settings."
3. In the left sidebar, click on "Developer settings."
4. Click on "Personal access tokens," then "Generate new token."
5. Add a descriptive note for the token (e.g., "GhostWriter Integration"), and select the "repo" scope.
6. Click "Generate token" at the bottom of the page.
7. Copy the generated token, as you won't be able to see it again.

### For GitLab:

1. Log in to your GitLab account.
2. Click on your profile picture in the top-right corner and select "Settings."
3. In the left sidebar, click on "Access Tokens."
4. Add a name and optional expiration date for the token (e.g., "GhostWriter Integration").
5. Select the "read_repository" scope.
6. Click "Create personal access token."
7. Copy the generated token, as you won't be able to see it again.

### For Bitbucket:

1. Log in to your Bitbucket account.
2. Click on your profile picture in the bottom-left corner and select "Personal settings."
3. In the left sidebar, click on "SSH keys."
4. Generate a new SSH key using a tool like `ssh-keygen` and copy the public key.
5. Click "Add key" and paste your public key into the "Key" field.
6. Add a label for the key (e.g., "GhostWriter Integration") and click "Add key" again.

## Step 2: Add Git Repository to GhostWriter

Now that you have an access token or SSH key, you can add your Git repository to GhostWriter:

1. Log in to your GhostWriter account.
2. Navigate to the "Integrations" or "Connections" section.
3. Click "Add Integration" or "Connect Repository," and select your Git provider (GitHub, GitLab, or Bitbucket).
4. Enter the required information, such as the repository URL and your access token (or SSH key for Bitbucket).
5. Click "Add" or "Connect" to complete the integration process.

## Step 3: Configure GhostWriter Settings

After successfully connecting your Git repository, you may need to configure additional settings in GhostWriter to ensure proper content generation:

1. Select the relevant project or create a new one in GhostWriter.
2. In the project settings, ensure that your Git repository is selected as the source for your site's code.
3. Configure any additional settings as needed, such as content templates, style guides, or branch preferences.
4. Save your changes.

GhostWriter should now have access to your Git repository and be able to read your site's code to generate documentation. As you update your codebase, GhostWriter will automatically keep your documentation in sync with the latest changes.

# How to Set Up an Integration Between GhostWriter and Jira

This how-to guide will walk you through the process of integrating GhostWriter with your Jira instance. By connecting GhostWriter to Jira, you'll enable seamless collaboration between your documentation projects and your development tasks. Follow these steps to establish a secure connection between GhostWriter and your Jira instance.

## Prerequisites

1. A GhostWriter account
2. A Jira account (Cloud or Server)

## Step 1: Generate an API Token (Jira Cloud) or Create an Application Link (Jira Server)

First, you'll need to create an API token (for Jira Cloud) or set up an application link (for Jira Server) to authenticate GhostWriter's connection to your Jira instance.

### For Jira Cloud:

1. Log in to your [Atlassian account](https://id.atlassian.com/manage/api-tokens).
2. Click on "API tokens" in the left sidebar, then "Create API token."
3. Add a descriptive label for the token (e.g., "GhostWriter Integration").
4. Click "Create" and copy the generated token, as you won't be able to see it again.

### For Jira Server:

1. Log in to your Jira instance as an administrator.
2. Click on the gear icon in the top-right corner and select "Applications."
3. In the "Integrations" section, click on "Application links."
4. Enter the URL of your GhostWriter instance and click "Create new link."
5. Complete the "Link applications" form, providing a descriptive name (e.g., "GhostWriter Integration") and leaving other fields as default.
6. Click "Continue" to create the application link.

## Step 2: Add Jira Integration to GhostWriter

Now that you have an API token or an application link, you can connect your Jira instance to GhostWriter:

1. Log in to your GhostWriter account.
2. Navigate to the "Integrations" or "Connections" section.
3. Click "Add Integration" or "Connect Project Management Tool" and select "Jira."
4. Enter the required information, such as your Jira instance URL, email address (for Jira Cloud), and API token (or OAuth credentials for Jira Server).
5. Click "Add" or "Connect" to complete the integration process.

## Step 3: Configure GhostWriter Settings

After successfully connecting your Jira instance, you may need to configure additional settings in GhostWriter to ensure seamless collaboration between your documentation projects and development tasks:

1. Select the relevant project or create a new one in GhostWriter.
2. In the project settings, ensure that your Jira instance is selected as the project management tool.
3. Configure any additional settings as needed, such as mapping documentation statuses to Jira issue statuses or setting up custom issue types.
4. Save your changes.

GhostWriter should now have access to your Jira instance, allowing you to create, manage, and synchronize documentation tasks with your development tasks. As you update your tasks in Jira, GhostWriter will automatically reflect the changes in your documentation projects.