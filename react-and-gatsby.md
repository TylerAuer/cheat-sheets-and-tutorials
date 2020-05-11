# Notes for React and Gatsby

## Gatsby Command Line

- `gatsby new [SITE_DIRECTORY_NAME] [URL_OF_STARTER_GITHUB_REPO]` - Create new site where starter the source of the intial files and contents. Can be omitted for default starter.
- `gatsby develop` - Begin watching files and host site at `localhost:8000`
- `gatsby build` - Creates a production build of the site

## Gatsby Components

- `<Link to="/contact/">Contact</Link>`

## Gatsby File Structure

- `/src/components` - reusable components such as the header live here
- `/src/pages` - Any components here are converted to pages by gatsby
- `/src/styles` - Home to global.css and other stylesheets (this location is arbitrary)
