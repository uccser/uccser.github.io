# Student Projects

Welcome to the UCCSER team, we are looking forward to seeing your work this year.
This page of documentation is to help you get setup within the team, and information specific to developing a student project.

## First Steps

We recommend you take the time to read the entirety of this documentation website, as it walks you through our contribution style, projects, and technical stack.

If you are not familiar with Django, we ask you complete the [Django tutorial](https://docs.djangoproject.com/en/dev/intro/) (up to part 7).
It does a great job of walking you through the main concepts of Django.

## Research and Test Deployments

It's likely at some point of your project you will want to test your website with users.
Our main projects have a 'research' workflow built in that allows running your modified project at a testing domain that's accessible to the public (since most of our testing happens remotely).

The following domains are set aside for research projects:

- [https://uccser-study-one.csse.canterbury.ac.nz](https://uccser-study-one.csse.canterbury.ac.nz/)
- [https://uccser-study-two.csse.canterbury.ac.nz](https://uccser-study-two.csse.canterbury.ac.nz/)
- [https://uccser-study-three.csse.canterbury.ac.nz](https://uccser-study-three.csse.canterbury.ac.nz/)
- [https://uccser-study-four.csse.canterbury.ac.nz](https://uccser-study-four.csse.canterbury.ac.nz/)
- [https://uccser-study-five.csse.canterbury.ac.nz](https://uccser-study-five.csse.canterbury.ac.nz/)
- [https://uccser-study-six.csse.canterbury.ac.nz](https://uccser-study-six.csse.canterbury.ac.nz/)

The modifications can be in an official UCCSER GitHub repository, or a fork from one of these repositories.

### Setup for deployment

**Note:** *Some websites (for example: codeWOF) have additional features or behaviours when in research mode, see the projects documentation for more information.*

The following steps need to be taken in order for a website to be deployed:

1.  If the repository is a fork from an official repository, then it should be updated to the latest commit on the `develop` branch.
    The `test-and-deploy` workflow on GitHub also needs permission to run (if it isn't already).

2.  A new git branch needs to be created off the branch that contains the changes to test.
    This branch must start with `research-study-`.
    This new branch will have specific commits for publishing the website and will never be merged back into the main branch the author is working on.
    If changes are made during research, then these are made on the branch you are working on, and pulled through to the special research branch.

3.  On the research branch, the `docker-compose.prod.yml` needs to be modified in the following places:

    -   The value for `x-django-config: image:` needs to be set to the image created by your repository.
        This is likely to be `ghcr.io/{YOUR_USERNAME}/{PROJECT_NAME}:{RESEARCH_BRANCH_NAME}`.
        For example, the value may be `ghcr.io/jackmorgannz/cs-unplugged:research-study-block-based-programming`
    -   Any `${PROJECT_DOMAIN}` values need to replaced with an available URL.
        For example, the value may be `uccser-study-four.csse.canterbury.ac.nz`.
    -   Any `${PROJECT_ROUTER_RULE}` values need to replaced with a valid Traefik routing rule.
        For example, the value may be `` Host(`uccser-study-four.csse.canterbury.ac.nz`) ``.
    -   Any traefik routers and services needs to be renamed so it doesn't conflict with existing websites Traefik settings.
        For example, if the existing compose file used `cs-unplugged-django` for its service and router, then replace all occurences with `uccser-study-four-django`.
    -   Any Docker `secrets` and `configs` need to be renamed so it doesn't conflict with existing values.
        For example, if the existing compose file contains the secret `cs-unplugged_django_secret_key`, then the secret should be renamed to `uccser-study-four_django_secret_key`.

4.  Push your `research-study-` branch, wait for the `test-and-deploy` workflow to complete on GitHub.
    Your package should now be available on GitHub (listed on the repository homepage).

5.  Ask a staff member who has permissions to the development swarm to deploy the website.

#### Staff notes

-   Clone the repository within the swarm within a directory for the research number.
    This avoids conflicts of two projects with the same name existing in the same directory.
-   All secret values need to created.
-   If the website contains an accessible admin interface, you will want to run `createsuperuser` to create an account for the student.
-   You also need to set the correct site domain under 'Sites' in the admin interface if emails are being sent to users.

### After deployment

If you need to make changes to the website once it's deployed, make the changes on your normal development branch, and then pull your changes into your `research-study-` branch.
This avoids any of the changes to the `docker-compose.prod.yml` entering into your final work.
Once you have pulled the changes through, wait for the `test-and-deploy` workflow to complete on GitHub, and then notify a staff member to redeploy your website.

Remember to ask the staff member to remove your website once your testing is completed.
You can also then delete your `research-study-` branch.

### After research

Once your reseach is concluded and you no longer require the research website, please inform a staff member who has permissions to the development swarm to remove the website.

#### Staff notes

- Remove the Docker Stack using `docker stack rm {STACK_NAME}` on a manager node.
- Remove the Docker Volumes of the stack on the database node (see [server-tools repository](https://github.com/uccser/server-tools) for details) as these will contain research participant's data and is not removed with the previous command.

## Group Logos

You may wish to use the logo for our group during your project, our logos are below:

- [Colour logo](/img/uc-computer-science-education-logo.png)
- [Black logo](/img/uc-computer-science-education-logo.png)
- [White logo](/img/uc-computer-science-education-logo.png)

## Final Report

We will ask permission to include your final report within our repository, as this aids future students and contributors.
