# Environment File

The environment file is used to inject variables into the container during the run process. This will be used to authenticate to the private git services and ensure the client can properly display the content.

Below is an example of the required environment file:

```
PORT=3000
HOST=localhost
PROTOCOL=http
VERBOSE=false
SQLITE_DATABASE=true

IS_PRIVATE=true
PROVIDER=bitbucket
GITHUB_USER=[ GITHUB USER ASSOCIATED WITH ACCESS TOKEN ]
GITHUB_ACCESS_TOKEN=[ GITHUB ACCESS TOKEN]
BITBUCKET_USER=[ BITBUCKET USER ASSOCIATED WITH APP PASSWORD]
BITBUCKET_PASSWORD=[ BITBUCKET APP PASSWORD]
```

- **PORT** - The port that the service will bind too. If used with docker, this is internal to the docker container. If the service is run through Node.js or PM2, this will be the port that will be used to connect to the running scraper. If this is left out, the port will default to 3000.
- **HOST** - The host at which the scraper will be available. This will be used to construct the raw content urls returned from the scraper.
- **PROTOCOL** - https or http. Currently, only http is supported.
- **VERBOSE** - Verbose logging. Used internally to the container. External logging is on the roadmap.
- **SQLITE_DATABASE** - True. Currently, the container uses an internal sqlite database. 
- **IS_PRIVATE** - Let's the scraper know that the repositories are private and require authentication.
- **PROVIDER** - Specifies which git service provider is going to be used. Below are the supported options:
    - github
    - bitbucket
- **GITHUB_USER** - User account associated with the generated access token.
- **GITHUB_ACCESS_TOKEN** - The Github access token for api calls and authentication. Only needs read access for the repositories.
- **BITBUCKET_USER** - User account associated with the generated app password.
- **BITBUCKET_PASSWORD** - App password with read access for the repositories.