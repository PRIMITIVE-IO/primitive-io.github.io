# Primitive Cloud Platform

Primitive's cloud platform allows analysis of your Git repositories on demand. Through your dashboard, you are able to create "scrapers" that connect to your online Git provider, pull information about the repo, and provide information back to the Primitive VR client. This process relies on access to the Git repositories and this is accomplished through application tokens generated within your Git service (e.g., Bitbucket, GitLab).

## App Passwords

Each Git platform provides the ability to generate scoped tokens to be used within applications or automation. These tokens or app passwords be be scoped to only allow certain privileges. As a general rule of thumb, Primitive needs to use tokens that have READ access to your repositories, and the associated APIs.

Because the access tokens are usually associated with individuals, Git admins or those with access to many different repositories should set up the "scraper." This allows the associated scraper visibility to each of the repositories that the user has permission to access. With that said, here are some recommendations when integrating Primitive's cloud platform into your Git service:

1. Have an admin generate the token to provide the greatest visibility into various repositories.
2. Create a new account with access to whichever repositories that are going to be analyzed by Primitive.
3. Make sure the app passwords are scoped properly (i.e., read-only access).
4. Be aware that admins of your scraper will have visibility into whichever repositories are associated with the account that created the app password.

For platform-specific information related to token/app password creation, please see below:

* [GitLab Access Tokens](/docs/cloud/gitlab-tokens.md)
* [Bitbucket App Passwords](/docs/cloud/bitbucket-tokens.md)

## General Troubleshooting

Because Primitive relies on a few APIs, there may be situations where the associated Git platform is unavailable or undergoing maintenance. This may affect the following actions:

1. Scraping repositories through the admin interface
2. Creating a new scraper via the cloud portal dashboard
3. Accessing repositories within Primitive once repo-level permission checking is enabled

As some of these are out of our control, please be patient with us as maintenance is completed or outages are resolved. If you are having issues with one of the above actions, reach out to support@primitive.io or confirm the underlying system is operational (Git status pages);

* [GitLab Status Page](https://status.gitlab.com/)
* [Bitbucket Status Page](https://bitbucket.status.atlassian.com/)
