# GGU-Software Organization Workflows

This repository contains shared workflow templates for the GGU-Software GitHub organization.

## Available Workflow Templates

### Trigger Jenkins Build

Workflow template for triggering Jenkins release builds from GitHub Actions.

**Location:** `workflow-templates/trigger-jenkins.yml`

**Features:**
- Manual workflow dispatch with input parameters
- Supports all GGU applications
- Optional approval step skip
- Integration with existing Jenkins build infrastructure

**Required Organization Secrets:**

Configure these secrets at the organization level:
- `JENKINS_URL` - The Jenkins server URL
- `JENKINS_USER` - The Jenkins username for API access
- `JENKINS_TOKEN` - The Jenkins API token

**Usage:**

1. Add the workflow template to your repository from the "Actions" tab
2. Configure the workflow inputs:
   - **app_name**: Application name (e.g., GGU-CONNECT, GGU-RETAIN)
   - **version**: Version number (e.g., 1.46, 4.8.1.2)
   - **skip_approval**: Whether to skip manual approval (default: false)
3. Run the workflow from the Actions tab

**Parameters:**

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
| app_name | Application name | Yes | - |
| version | Version number | Yes | - |
| skip_approval | Skip manual approval step | No | false |

**Security Notes:**

- The workflow requires Jenkins credentials to be configured as organization secrets
- By default, manual approval is required in Jenkins UI
- Skip approval only when explicitly needed and authorized

## Setting Up Organization Secrets

1. Go to organization settings: https://github.com/organizations/GGU-Software/settings/secrets/actions
2. Click "New organization secret"
3. Add the following secrets:
   - Name: `JENKINS_URL`, Value: Your Jenkins server URL
   - Name: `JENKINS_USER`, Value: Your Jenkins username
   - Name: `JENKINS_TOKEN`, Value: Your Jenkins API token
4. Configure repository access for the secrets

## Using Workflow Templates

When creating a new workflow in any repository:

1. Go to the repository's "Actions" tab
2. Click "New workflow"
3. Select "trigger-jenkins.yml" from the organization templates
4. Customize if needed and commit

## Support

For issues or questions about these workflow templates, please contact the GGU development team.
