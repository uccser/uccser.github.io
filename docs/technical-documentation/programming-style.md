# Programming Style

## Git

- Commits should be as descriptive as possible.
  Other developers (and even future you) will thank you for your forethought and verbosity for well documented commits.
  Generally:

  - Limit the first line to 72 characters or less
  - Reference issues and pull requests liberally


## GitHub

- Mention a user (using the `@` symbol) when an issue is relevant to them.
- Only assign yourself to an issue, when you are actively working on it.
- The technical team may tag an author to review specific pull requests, and as a reviewer you can either approve, request changes, or just leave comments.
- A pull request requires one review approval to be merged.
- If multiple people are tagged as reviewers, we only need one review (unless otherwise specified).
  For example: For content changes, we ask that at least one member from each of the content and technical teams reviews the pull request.
- The creator of the pull request should assign all those suitable for review.
- The creator of the pull request is the only person who should merge the pull request.
  If you approve a pull request and it shows the big green button, please resist clicking it!

## Project Structure

- Directories should be all lowercase with dashes for spaces.
- Directories and files should use full words when named, however JavaScript, CSS, and image directories can be named ``js/``, ``css/``, and ``img/`` respectively.

## Text (Markdown)

- Each sentence should be started on a newline (this greatly improves readability when comparing two states of a document).

## Programming

Quote from Google style guides:

> Be consistent.
>
> If you’re editing code, take a few minutes to look at the code around you and determine its style.
> If they use spaces around all their arithmetic operators, you should too.
> If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.
>
> The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it.
> We present global style rules here so people know the vocabulary, but local style is also important.
> If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it.
> Avoid this.

We also recommend reading Python's PEP008 introduction: [A Foolish Consistency is the Hobgoblin of Little Minds](https://peps.python.org/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds)

We aim to abide by the following style guides:

### Python

We follow [PEP8](https://peps.python.org/pep-0008/) (except for one change of line length) and [PEP257](https://peps.python.org/pep-0257/).
Django recommends [allowing 119 characters](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/), so we use this as our line length limit.
These styles are enforced by the `flake8` style checker.

We also have a tool for checking docstrings.
This only performs basic tests, like if the docstring is available.
Multi-line docstrings consist of a summary line, followed by a blank line, followed by a more elaborate description.
Single line docstrings are allowed, but we ask you make docstrings as descriptive as possible.

### HTML

We follow the open source [Code Style Guide](https://codeguide.co/#html) by [@mdo](https://markdotto.com/).

### CSS/SCSS

We follow the open source [Code Style Guide](https://codeguide.co/#css) by [@mdo](https://markdotto.com/).

### JavaScript

We follow the [Google JavaScript style guide](https://google.github.io/styleguide/jsguide.html) with 2 or 4 space indentation.
