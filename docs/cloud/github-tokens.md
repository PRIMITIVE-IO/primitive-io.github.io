# GitHub Access Tokens

GitHub Access Tokens are used to connect applications to your Git repositories. For information related to creating app passwords, please see the following documentation:

* [GitHub Personal Access Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

Once an app password is created, it can NOT be accessed again. Ensure this value is saved somewhere SECURE in case it is needed again. If a new one needs to be regenerated to create a new scraper, change credentials, or be rotated, ensure the old app password is revoked.

## App Password Creation

1. Go to <a href="https://github.com/settings/tokens/">github.com/settings/tokens</a>
    * This can be accessed via 'Profile' on the top right -> Settings -> Developer settings on the bottom left -> Personal access tokens
2. Provide a meaningful token name
    * The label will help keep track of what app password is used for what application. This simplifies the process of revoking passwords when needed and eliminates guessing.
4. Make sure the following permissions are selected:
    * `public_repo`
    * `read:org`
    * `read:user`
    * `read:project`
5. Select `Generate token`
6. Securely store or take note of the app password presented after creation
    * This app password will not be shown again. If this is accidentally closed before copying, revoke it, and create a new one

An expiration can also be added if needed. If the integration is expected to be long-term, this is not recommended as it may silently fail when the token expires and cause issues within Primitive.

## Primitive Permissions

These permissions are used to access what repositories you have access to analyze, information on permissions, and to clone the repository in order to complete the code analysis.

<p><img src="/_media/githubAccessTokenCreation.png" style="width: 90%; border: 1px solid #000;"></p>