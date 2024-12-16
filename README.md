## Configuring AWS Credentials

1. Add OIDC Provider for Github Actions

Github actions requires a role to use to access your AWS resources when pushing/pulling your sst app. This is configured through OIDC and is the recommended approach as opposed to using access keys.

To do this, go to the IAM console, under Identity Providers and add choose Add Provider

Set the Provider URL as `https://token.actions.githubusercontent.com`

Set the Audience as `sts.amazonaws.com`

2. Create an IAM Role

Next, you will need an IAM role to use the identity provider created above. This is role that will be used when deploying. While still under the IAM console, head to roles then proceed to create a new one

Select `Web Identity` as the entity type then select the identity provider and audience we just created. Finally, set the name of your github organization. Repository and branch are optional.

In the next step, under permissions, add the `AdministratorAccess` policy then review and create the role.

You can read more on configuring AWS credentials for Github Actions [here](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)