# Search within a Specific Site from Address Bar

Chromium based system allow for adding custom shortcut that can be trigger from address bar. For instance, if I want to search something in GitHub, I don't need to go to `github.com` and then click on search and then type it. I can simply do the following.

- Open a new tab
- Trigger the shortcut which is based on some keys. For me it's `@g`.
- Press that to activate the shortcut.
- Enter the search keywords and submit it by pressing enter.

## Setup

- Open the settings in the browser and look for `Manage search engines and site search`. 
- In that you will find a `Site search` section. 
- Click on `add`
- It will ask you for some details
    - `name`: You can name it whatever you want. Won't really matter as it doesn't affects the functionality.
    - `Shortcut`: This is what you will use to prompt the address bar.
    - `URL with %s in place of query`: This is the URL that has the endpoint to search within the site. 

## Example

- `name`: `GitHub`
- `Shortcut`: `@g`
- `URL with %s in place of query`: `https://github.com/search?q=%s`

---
