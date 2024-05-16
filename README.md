# Setup

- This GitHub Pages site uses the [Reverie](https://github.com/amitmerchant1990/reverie) theme.
  - Non-gem-based theme.
  - Fork of [jekyll-now](https://github.com/barryclark/jekyll-now).
- This page describes the steps taken to create a clean site using this theme.

## Apply Theme

- Use the Reverie template repo to create a new GitHub repo.
  - Use the "Use this template" link at <https://github.com/amitmerchant1990/reverie?tab=readme-ov-file#1-fork-reverie-to-your-user-repository>.
  - Give the repo a name (`notes`) and create the repo.
  - Edit `_config.yml`:
    - replace `baseurl: "/reverie"` with `baseurl: "/notes"` (i.e., the repo name).
- Select the "Actions" tab on GitHub to see the pages being built and deployed.
- When deployed, go to `https://`_`username`_`.github.io/notes/` to confirm the site has been built correctly, including its links.

## Local Development

- Prerequisite: [Ruby](https://jekyllrb.com/docs/installation/)
- Clone the repo.
- Install the gems:
  - `bundle install`
- Build and run the site:
  - `bundle exec jekyll serve`
- Confirm the site is built correctly, including its links.
  - <http://localhost:4000/notes/>.
