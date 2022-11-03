# Technical Stack and Structure

This page provides details around the technical stack we use and how it is structured.
These are just general details that apply to *most* of our projects.

## General

There are two main aspects that drive our technical stack choices, *accessibility* and *usability*.

### Accessibility

Accessibility is best explained using the [Wikipedia definition](https://en.wikipedia.org/wiki/Web_accessibility):

> Web accessibility, or eAccessibility, is the inclusive practice of ensuring there are no barriers that prevent interaction with, or access to, websites on the World Wide Web by people with physical disabilities, situational disabilities, and socio-economic restrictions on bandwidth and speed.
> When sites are correctly designed, developed and edited, more users have equal access to information and functionality.

The socio-econmic restrictions can be quite prevalent in our target audience of students in classrooms, which may have older devices with low resources.
For this reason we aim for our systems to do the hard work where possible, instead of user's devices doing the work.
We use server side rendering of webpages, compared to JavaScript frameworks (e.g. React, Vue) which perform the rendering on the users device.

We currently don't meet specific accessibility guidelines (e.g. [WCAG](https://www.w3.org/TR/WCAG21/)) but work towards these where possible.

### Usability

We aim for our projects to be easily understandable and logical for our users.
Our websites will often look 'simple' from a glance, but that is avoid any confusion in their purpose.
For example, we don't use many transitions or animations for pages, instead favoring instant feedback options (for example, changing the background colour of a link button upon hovering).

## Backend

We use Docker to ensure our systems run the same in all locations (both for development and after deployment).
We use Docker Compose to connect Docker container together for local development.

We primarily develop in Python, in particular using the [Django framework](https://www.djangoproject.com/).
We aim to create and clear Django system for ease of development.
We are using some advised patterns and practices from [Two Scoops of Django by Feldroy](https://www.feldroy.com/), which includes (but isnot limited to the following):

- Locking versions of dependencies.
- Django secret settings are loaded from environment variables or Docker secrets.
- The base Django directory, containing settings and base `urls.py` is called `config/`.
- Settings files are separated for different usages.
- All templates are located in the `templates/` directory.

We use Markdown as the language for text content as it has a great balance between simplicity of writing for authors, and clear structure when converting to HTML.
We have written additional Markdown tags for complex elements in a Python Package called [Verto](https://github.com/uccser/verto).

We use YAML for storing configuration data.
It has improved human readability over JSON and XML, especially for authors who have no or little experience with configuration files.

We try to avoid deep nesting (indentation) within configuration files as it's harder for authors to read nested data.
We have split configuration data across multiple configuration files to avoid this issue.

We store our content within the source code of the system, so both are versioned together.
We also store our documentation within the same respository for the same reason.
This prevents the content, system, and documentation don't become out of sync easily.

To populate a Django database with content we use custom content loaders.
The loaders for an application are generally found in the `management/commands/` directory of a Django application.
Besides populating fields in the database, a loader is also responsible for checking that its corresponding configuration file contains all the required fields, Markdown files are not empty, and icons can be found.
If any of these conditions are not met, then an error is thrown.
Errors are defined in `utils/errors/` and should aim to be as descriptive and useful~as possible as they will most often be read by an author and not necessarily a Python developer.
The loaders will update existing content if it is already present, however it doesn't have logic to detect if any content needs to be deleted.
This is because we rarely delete content from our websites, and if content needs to be deleted then it can either be removed via the administrator interface (codeWOF, DTHM for Kaiako) or via a Django shell on the deployment (CS Unplugged, Computer Science Field Guide).

We use Postgres as our database.

Our search features use the Full Text Search (FTS) built into Postgres.

We support internationalisation (i18n) and localisation (L10n) by default.
See our [documentation page on internationalisation](internationalisation.md) for more information.

## Frontend

We use the [Django Templating Engine](https://docs.djangoproject.com/en/dev/topics/templates/) to render HTML pages server side.
We use [Bootstrap 4](https://getbootstrap.com/docs/4.6/getting-started/introduction/) as the framework for developiong responsive websites.
We write additional CSS using SCSS.

We use a Gulp pipeline to process our static files.

## Local Development

There are two major tools we use for assisting in local development in most of our projects:

1. We use our [UCCSER Development Stack](https://github.com/uccser/uccser-development-stack) for running a proxy on your machine for accessing a website via HTTPS.
   This matches the setup in the production environment.
   The stack also has [Mailhog](https://github.com/mailhog/MailHog) installed, so if you trigger an email in local development it is caught by the system and can be viewed at [email.localhost](https://email.localhost/).
2. We use a helper script called `dev` (found in the project root directory) for providing aliases to long sequences of commands.
   For example, instead of having to enter multiple commands for generating static files, migrating the database, loading content, etc, the helper script can run these with `./dev update`.
   If the `dev` script is available, running `./dev help` will output all the available options.

## Deployments

We use Docker Swarm to deploy our websites.
We have two swarms hosted at the University of Canterbury, one for production websites and one for staging websites.

The development swarm has automated tasks for pruning unused containers, images, and volumes.

The production swarm requires deployments to be done manually.
