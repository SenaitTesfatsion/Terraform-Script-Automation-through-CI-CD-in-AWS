# Automating Terraform Script Deployment with AWS CodeBuild

This project showcases the automation of infrastructure updates managed by Terraform through the setup of an AWS CodeBuild project. AWS CodeBuild is integrated with GitHub to streamline the deployment process seamlessly and efficiently.
## Prerequisites

Before setting up the CodeBuild project, ensure the following prerequisites are met:

- **AWS Account**: You need access to an AWS account with permissions to create and manage CodeBuild projects.
- **GitHub Repository**: The Terraform scripts must be stored in a GitHub repository.
- **Terraform Installed**: Install Terraform on the CodeBuild environment to execute the scripts.

## Setup Steps

### 1. Create a CodeBuild Project

1. Go to the AWS Management Console and navigate to the CodeBuild service.
2. Click on "Create build project".
3. Configure the project settings:
   - **Project name**: Choose a name for your CodeBuild project.
   - **Source provider**: Select "GitHub" and connect your GitHub account.
   - **Repository**: Choose the GitHub repository containing your Terraform scripts.
   - **Environment**: Specify the runtime environment for CodeBuild, including the Docker image with Terraform installed.
   - **Buildspec**: Create a `buildspec.yml` file that defines the build steps, including Terraform commands for initialization, planning, and applying changes.
   - **Artifacts**: Configure artifact storage if needed.
4. Click on "Create build project" to create the CodeBuild project.

### 2. Set up GitHub Webhook

1. In your GitHub repository, navigate to "Settings" > "Webhooks".
2. Click on "Add webhook".
3. Set the Payload URL to the webhook endpoint provided by CodeBuild.
4. Configure the webhook settings (e.g., content type, events to trigger the webhook).
5. Save the webhook configuration.

### 3. Configure IAM Roles

Ensure the CodeBuild service role has permissions to access the necessary AWS resources (e.g., S3 buckets, EC2 instances) and execute Terraform commands.

### 4. Test the Integration

Make a change to your Terraform scripts and commit the changes to the GitHub repository. This should trigger the CodeBuild project to automatically apply the Terraform changes.

## Monitoring and Troubleshooting

- Monitor the CodeBuild project executions in the AWS Management Console.
- Check the build logs for any errors or issues encountered during the Terraform execution.
- Use CloudWatch Logs for detailed logging and monitoring.

## Security Considerations

- Ensure proper IAM permissions are assigned to the CodeBuild service role to prevent unauthorized access to AWS resources.
- Implement least privilege principles when configuring IAM roles for CodeBuild.
- Secure sensitive information such as AWS credentials and secrets using AWS Secrets Manager or Parameter Store.
