# Private Scraper Usage

## Scraper Admin Interface

The scraper interface can be broken down into two main functions: scraping new repositories, and managing previously scraped ones.

#### Scraping New Repositories

At the top of the admin panel, there is a text field labeled 'Repository URL' with a 'Scrape Repo!' button. To scrape a new repository within your private infrastructure, input the http/https clone url in the text field and press the scrape button. It's that easy! There are a couple of notes here...
- The http/https clone url should not include your username. The url should be in the format **[baseurl]/[organization/owner]/[project name]**.
- The base url can include the protocl (http/https) and the associated port (7990/3000/etc).

#### Managing Existing Repositories

Once a repository is scraped and ready for the client, you will see a "complete" message within the status bar at the bottom of the page. On a page refresh, the newly scraped repository should appear in the Repo table.

Once in the repo table, you will have the ability to edit the metadata of the repository for display within the Primitive Client, remove the repository, requeue the repository, and view the current data saved.

##### Requeue

Requeuing removes the current cache entry and re-scrapes the repository. This can be done to update the repo in the Primitive client to the most recent version pushed to your master branch.

##### Remove

Removing the repository removes the repo data from the scraper. This removes the ability for the Primitive client to graph the codebase and the repository must be re-scraped in order to restore this ability.

##### Repository Values

The repository values include a tag, layer, and enabled field. 

| Value        | Description  |
| ------------- |:-------------|
| **Repo**      | The repository url that represents the scraped data. This should resemble the http/https clone url. There should be no username within the url and the '.git' can be removed. This is for standardization across git platforms. |
| **Tag**     | The tag is the group label used to organize the repositories within the Primitive environment. Each tagged repository will be grouped based on their tag for easier navigation of the codebases |
| **Layer**     | The layer is the value associated with which level the repository is placed in. The core of the Primitive structure is layer 0 and the layer number increments as you move away from the center. -1 is the default which puts it on the outer layer.  |
| **Enabled** | The enabled flag allows you to remove the repository from the Primitive environment without deleting the data. A value of '0' disables the repository where a value of '1' enables it. |

#### Repository Preview

The image that you see at the top of the model is a quick preview of what the codebase structure looks like. This is used as a starting point in the visualization process and becomes the foundation of the VR structure. If there is no preview present, something may have gone wrong. Please check that the URL is correct and there is no connectivity issues.

##### Repository Links

The links included in the modal represent the data being consumed by the Primitive client. All other information pertaining to the repository are streamed into the client on demand.

