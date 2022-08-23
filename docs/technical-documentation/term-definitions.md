# Term Definitions

There are several terms we use throughout our projects.
We have defined them here.

## Application

We when use the term application, it generally refers to a package/component of a Django project.
Each large part of a project is a separate application.
Each application has its own directory within the project folder.
For example, in the CS Unplugged project, the following are applications:

- `topics`
- `plugging_it_in`
- `resources`
- `search`

The `config` application is a special application created upon project generation and contains the core project settings.

## Slug

Slugs are a text value containing only lower case letters, numbers, and hyphens.
We generally use them as unique identifiers, and used in URLs.

These are *valid* examples of keys:

- ``algorithms``
- ``binary-numbers``
- ``challenge-2``

These are *invalid* examples of keys:

- ``Algorithms``
- ``Binary Numbers``
- ``Binary_Numbers``
- ``binary_numbers``
- ``challenge 2``

See also the [definition of URL slug on Wikipedia](https://en.wikipedia.org/wiki/Semantic_URL#Slug).
