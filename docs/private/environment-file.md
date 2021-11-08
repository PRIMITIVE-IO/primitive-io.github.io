# Environment File (config.json)

The config file is used to set the required variables and values for the scraper to run. This is now a JSON file that is added to the `data` folder which is mounted to the host. This will be used to authenticate to the private git services and ensure the client can properly display the content.

Below is an example of the required config file:

```
{
    "PORT": 443,
    "HOST": "{{ scraper_host }}",
    "PROTOCOL": "https",
    "VERBOSE": true,
    "SQLITE_DATABASE": true,
    "IS_PRIVATE": true,
    "PROVIDER": "{{ provider }}",
    "BASE_URL": "{{ base_url }}",
    "GITHUB_USER": "{{ github_user }}",
    "GITHUB_ACCESS_TOKEN": "{{ github_token }}",
    "BITBUCKET_USER": "{{ bitbucket_user }}",
    "BITBUCKET_PASSWORD": "{{ bitbucket_token }}",
    "GERRIT_USER": "{{ gerrit_user }}",
    "GERRIT_PASSWORD": "{{ gerrit_token }}",
    "GENERATE_DATABASE": true,
    "TEMP_DIR": "/tmp",
    "OUTPUT_DIR": "/home/scraper/data",
    "ANALYZERS":[
        {"name": "dotnet-parser", "image_name": "xxxxxxxxx.dkr.ecr.us-east-2.amazonaws.com/dotnet-parser:prod-0.1.23", "extensions": [".cs", ".h", ".hxx", ".hpp", ".cpp", ".c", ".cc", ".m", ".py", ".py3", ".js", ".jsx", ".kt", ".ts"]}
    ],
    "UPDATE_PERMS": false,
    "ROOT_PASS":"",
    "SSL_KEY": "{{ ssl_key }}",
    "SSL_CERT": "{{ ssl_cert }}",
    "SSL_CA": "{{ ssl_ca }}"
}
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
- **TEMP_DIR** - The temporary file used during various processes in the scraper container. We usually use '/tmp' but this can be configured to something different.
- **OUTPUT_DIR** - This is the local folder used to mount the container to the local file system. This will be shared between containers and therefore must be defined externally via the configuration file.
- **ANALYZERS** - This is an array of json objects representing which parsers are available for the scraper. This includes the name, the image_name, and the extensions. The name is used internally and is usually just set to the parser name without the repo URL. The image name is what the actual name of the image is in the local docker environment. The extensions specifies which filetypes should be associated with that specific parser. If the extensions array is empty, no filetypes will be associated with that parser and it will NOT be run on project files.
- **UPDATE_PERMS** - This can update the permissions of the scraper DBs if the scraper is run in a different permission that the parsers. This can be used during debugging or during development if the debugger being leveraged does not run as root.
- **ROOT_PASS** - Used primarily during testing, this is used if the above variable is true (UPDATE_PERMS). This should be empty under normal deployments.
- **SSL_KEY and SSL Variables** - Absolute file path of the ssl certs associated with the scraper. These are the files within the certs directory mounted to the container within the data directory.