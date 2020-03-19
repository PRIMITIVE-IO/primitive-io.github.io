# Volume and Data Persistence

The scraper pulls data from the git service and generates assets and cache entries for the client. These assets and cache entries exist outside of the container for data persistence. Within the specified folder, you will see one Sqlite database file and a series of folders that represent the scraped repositories. These assets container filenames, directory structures, and data used for preview generation. 

!> NO SOURCE CODE IS SAVED OUTSIDE THE CONTAINER

During the scrape, the project is downloaded into the container into a temporary directory. This directory is deleted as soon as the files are crawled and the relevant data is saved.

Before running the container, determine where this data will live and note the location for the run command when deploying the container. If the service is run outside of docker, the 'data' folder is required in the root of the project.