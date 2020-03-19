# Troubleshooting

| Issue                | Possible Solution |
| -------------------- | ----------------- |
| Preview is blank | The preview might be blank if the scrape was interrupted, or an error occured. This could be from the process being rate limited, the URL being incorrect, or network connectivity. Please check the URL and ensure it is in the correct format, make sure that the rate limits on your git service are appropriately set, and confirm that the scraper can access the git service |
| Some assets are not present (Repository links result in 404) | See above issue. This could also be caused by rate limiting issues, incorrect URLS, and/or network connectivity |
| Assets are valid but source code is unavailable in the client. | The base url could be incorrectly set in the scrapers configuration. Check to see that the 'url' value within the 'Package Data Url' is valid and points to the appropriate resource. |
| Client is unavailable to view source code and raw URLS are valid | Ensure that the client is properly authenticating to the git service. Source code is streamed from the git service to the Primitive client and is not handled by the scraper. Please check the credentials within the client to ensure proper authentication is occuring. |
| Raw URLS are malformed | Please check the environment file used to configure the scraper during setup. The 'provider' and 'base url' values should be validated to ensure the scraper is properly configured.

## Contact Us

If issues are unabled to be resolved, please contact us at **support@primitive.io**. 