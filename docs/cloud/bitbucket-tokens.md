# Bitbucket App Passwords

Bitbucket app passwords are used to connect applications to your Git repositories. For information related to creating app passwords, please see the following documentation:

* [Atlassian Support for App Passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)

Once an app password is created, it can NOT be accessed via Bitbucket. Ensure this value is saved somewhere SECURE in case it is needed again. If a new one needs to be regenerated to create a new scraper, change credentials, or be rotated, ensure the old app password is revoked.

## App Password Creation

1. Go to <a href="https://bitbucket.org/account/settings/app-passwords/">bitbucket.org/account/settings/app-passwords</a>
    * This can be accessed via 'Profile' on the top right -> Settings -> Personal settings -> App passwords
2. Select `Create app password`
3. Provide a meaningful label
    * The label will help keep track of what app password is used for what application. This simplifies the process of revoking passwords when needed and eliminates guessing.
4. Make sure the following permissions are selected:
    * `Account: Read`
    * `Workspace membership: Read`
    * `Projects: Read`
    * `Repositories: Read`
5. Select `Create`
6. Securely store or take note of the app password presented within the pop-up
    * This app password will not be shown again. If this is accidentally closed before copying, revoke it, and create a new one

## Primitive Permissions

Primitive requires READ access to:

* Account
* Workspace Membership
* Projects
* Repositories

These permissions are used to access what repositories you have access to analyze, information on permissions, and to clone the repository in order to complete the code analysis.

<p><img src="/_media/bitbucketAppPasswordCreation.png" style="width: 90%; border: 1px solid #000;
"></p>
