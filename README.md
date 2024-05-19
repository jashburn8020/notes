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
- Install gems:
  - `bundle install`
- Build and run the site:
  - `bundle exec jekyll serve`
- Confirm the site is built correctly, including its links.
  - <http://localhost:4000/notes/>.

## Repo-Specific Items

- Remove [sponsor buttons](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/displaying-a-sponsor-button-in-your-repository) on the repo.
  - Remove `.github/FUNDING.yml`.
  - Repo > Settings > General > uncheck "Sponsorships".
- Update [LICENSE](LICENSE).
- Remove `.ruby-version`.

## Favicon

- Remove the default favicon images:
  - `favicon.ico`
  - `images/favicon-32x32.png`
- Create your favicons, e.g., using <https://favicon.io/favicon-generator/>.
- Put the new favicons into [`images`](images).
  - Note: If the new favicons include a `site.webmanifest` file, ensure the file's icon `src`s point to the right location and update other details accordingly.
- Update [`_layouts/default.html`](_layouts/default.html) to point to the new favicons.

## Title, Header, and Footer

- Update site `name` in [`_config.yml`](_config.yml).
- Update site `description` in [`_config.yml`](_config.yml).
- Change site `avatar` (logo) in [`_config.yml`](_config.yml).
  - Replace default site avatar: `images/reverie.png`
  - If removing the site avatar:
    - remove `site-avatar` class in [`assets/style.scss`](assets/style.scss)
    - remove `site.avatar` variable in [`_includes/meta.html`](_includes/meta.html)
    - remove `avatar` variable in [`_config.yml`](_config.yml)
    - remove the corresponding HTML code in [`_layouts/default.html`](_layouts/default.html)
- Update site `author` in [`_config.yml`](_config.yml).
  - Replace `author` `{{ site.name }}` with `{{ site.author }}` in [`_includes/meta.html`](_includes/meta.html).
- Update `footer-links` in [`_config.yml`](_config.yml).
  - An empty value under the `footer-links` mapping will omit the corresponding footer icon as implemented in [`_includes/svg-icons.html`](_includes/svg-icons.html).

## Fonts

- Select a font from [Google Fonts](https://fonts.google.com/) and get the font's embed code.
  - Add the font's embed code to [`_layouts/default.html`](_layouts/default.html).
- Replace existing font stacks in [`_sass/_variables.scss`](_sass/_variables.scss) with a new font stack that includes the selected font.
  - Switch references to the existing font stack in [`assets/style.scss`](assets/style.scss) to the new font stack.
- Update font settings in [`assets/style.scss`](assets/style.scss).
  - Remove redundant (font) import at-rule.
  - Replace existing `font-family` values with the new font stack.
