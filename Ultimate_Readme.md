# The Ultimate Guide to Updating This Portfolio

This guide explains how to update Dipanjyoti Paul's portfolio without needing to understand Jekyll first. Follow one small section at a time.

## 1. The one rule to remember

Most information is stored in simple text files. Open the correct file, change only the words you need, save it, test the website, and then push the change to GitHub.

Do not edit files inside these generated or downloaded folders:

- `_site/` — a temporary built copy of the website.
- `vendor/` — downloaded Ruby packages.
- `node_modules/` — downloaded JavaScript packages.
- `.jekyll-cache/` — temporary Jekyll data.

Anything changed in those folders can disappear during the next build.

## 2. Where everything lives

| What you want to change                         | File or folder                         |
| ----------------------------------------------- | -------------------------------------- |
| Name, website address, footer, feature switches | `_config.yml`                          |
| Home/About page text                            | `_pages/about.md`                      |
| CV information shown on the website             | `_data/cv.yml`                         |
| Downloadable CV PDF                             | `assets/pdf/Dr_Dipanjyoti_Paul_CV.pdf` |
| Profile photograph                              | `assets/img/dipanjyoti-paul.jpg`       |
| Publications                                    | `_bibliography/papers.bib`             |
| Projects page settings                          | `_pages/projects.md`                   |
| Individual projects                             | `_projects/*.md`                       |
| GitHub repositories shown on the site           | `_data/repositories.yml`               |
| Social links and contact icons                  | `_data/socials.yml`                    |
| Blog placeholder or future blog landing page    | `_pages/blog.md`                       |
| Teaching page                                   | `_pages/teaching.md`                   |
| People page                                     | `_pages/people.md`                     |
| Navigation dropdown                             | `_pages/submenus.md`                   |
| Bookshelf placeholder                           | `_pages/books.md`                      |
| Windows-only development settings               | `_config.windows.yml`                  |
| GitHub deployment recipe                        | `.github/workflows/deploy.yml`         |

## 3. How a page file works

A page normally starts with a block between two lines containing `---`. This is called front matter.

```yaml
---
layout: page
title: teaching
permalink: /teaching/
nav: true
nav_order: 6
---
Write the visible page content here.
```

The important fields are:

- `title` is the word shown in the navigation bar and page heading.
- `permalink` is the page address after `/dipanjyoti`.
- `nav: true` puts the page in the navigation bar.
- `nav: false` keeps the page out of the main navigation.
- `nav_order` controls its position. A smaller number appears earlier.

Never delete either `---` line. Use spaces, not tabs, inside YAML.

## 4. Update the Home/About page

Open `_pages/about.md`.

### Change the short line under the name

Edit the `subtitle` value near the top:

```yaml
subtitle: Assistant Professor, University of Tsukuba · Visiting Scientist, The Ohio State University
```

### Change the biography

Edit the paragraphs below the second `---` line. Normal Markdown works here:

```markdown
This is a normal paragraph.

This text is **bold** and this is a [link](https://example.com/).
```

### Change the office information beside the photograph

Edit the indented HTML under `profile` and `more_info`:

```yaml
profile:
  more_info: >
    <p>Department name</p>
    <p>Institute name</p>
    <p>University and country</p>
```

### Change the home-page research interests or appointments

Find the `## Research interests` or `## Current appointments` heading and edit the bullet points below it. A Markdown bullet begins with `- `.

## 5. Update the CV page

The web CV is controlled by `_data/cv.yml`. The PDF download is a different file; updating one does not update the other.

### Contact information

At the top of `_data/cv.yml`, edit values such as:

```yaml
name: Dipanjyoti Paul
label: Assistant Professor · Machine Learning Researcher
email: example@university.edu
location: Tsukuba, Ibaraki, Japan
summary: A short professional summary.
```

Keep a space after every colon.

### Add an experience

Under `Experience:`, copy one complete entry, paste it in the correct chronological position, and change its values:

```yaml
- company: University name
  position: Job title
  location: City, Country
  start_date: 2026-04
  end_date: present
  summary: One short description of the role.
```

The leading `-` begins a new entry. Keep the other lines aligned beneath it.

### Add education

Under `Education:`, use this pattern:

```yaml
- institution: University name
  location: City, Country
  area: Subject name
  studyType: Degree name
  end_date: 2026-05
  highlights:
    - "Thesis: Thesis title"
    - "Advisor: Advisor name"
```

### Edit research interests

Find `Research Interests:` and edit its list:

```yaml
Research Interests:
  - bullet: Machine Learning
  - bullet: Computer Vision
```

### Edit professional memberships

Find `Professional Memberships:` and use one line per organization:

```yaml
Professional Memberships:
  - bullet: Institute of Electrical and Electronics Engineers (IEEE)
  - bullet: Association for Computing Machinery (ACM)
```

### Replace the downloadable CV PDF

1. Name the new PDF `Dr_Dipanjyoti_Paul_CV.pdf`.
2. Open `assets/pdf/`.
3. Replace the old file with the new file using exactly the same name.
4. Test the CV download button.

If you choose a different filename, update `cv_pdf` in both `_pages/cv.md` and `_data/socials.yml`.

## 6. Change the profile photograph

1. Prepare a JPG photograph.
2. Name it `dipanjyoti-paul.jpg`.
3. Replace `assets/img/dipanjyoti-paul.jpg`.
4. Keep the filename in `_pages/about.md` unchanged.

Using the same filename is easiest because no other file needs editing.

## 7. Update publications

Open `_bibliography/papers.bib`. Each publication is one BibTeX block.

Example:

```bibtex
@article{paul2026example,
  title     = {The Full Paper Title},
  author    = {Paul, Dipanjyoti and Other, Author},
  journal   = {Journal Name},
  year      = {2026},
  doi       = {10.0000/example},
  selected  = {true}
}
```

Important rules:

1. Give every paper a unique key after `@article{`, such as `paul2026example`.
2. Separate fields with commas.
3. Put text inside `{curly braces}`.
4. Set `selected = {true}` only when the paper should also appear on the home page.
5. If there is no DOI or code link, omit that field instead of inventing one.

The Publications page automatically reads this file.

## 8. Update projects

Every file in `_projects/` is one project card. Existing examples show the supported format.

To create a project:

1. Copy a similar file in `_projects/`.
2. Give the copy a short lowercase filename, for example `new-model.md`.
3. Edit its front matter and description.

A typical project file looks like:

```yaml
---
layout: page
title: New Model
description: A short explanation of the project.
importance: 1
category: research
github: https://github.com/username/repository
---
Write a longer project description here.
```

Smaller `importance` numbers appear first. The `category` should remain `research` unless `_pages/projects.md` is also updated to display another category.

## 9. Update the Repositories page

Open `_data/repositories.yml`.

### Change the GitHub user

```yaml
github_users:
  - dipanjyoti
```

### Add or remove a featured repository

Edit the list under `github_repos`:

```yaml
github_repos:
  - dipanjyoti/INTR
  - dipanjyoti/another-repository
```

Use the exact `owner/repository` spelling from GitHub.

## 10. Update social links

Open `_data/socials.yml`. Add a username only when the account exists. Leave an unused service empty or remove its line.

The CV download icon uses:

```yaml
cv_pdf: /assets/pdf/Dr_Dipanjyoti_Paul_CV.pdf
```

After changing a social username, click its icon on the local website and verify that it opens the correct profile.

## 11. Update the unfinished pages

The Blog, Teaching, People, and Bookshelf pages currently contain:

```markdown
**To be updated.**
```

Open the matching file in `_pages/` and replace that line with real content when it becomes available. You may use headings, paragraphs, lists, and links:

```markdown
## Course title

- First item
- Second item

[Course website](https://example.com/)
```

## 12. Change the navigation bar

Pages appear in the navigation when their front matter contains `nav: true`.

The current order is:

1. About — automatically shown as the home page.
2. Blog — `nav_order: 1`
3. Publications — `nav_order: 2`
4. Projects — `nav_order: 3`
5. Repositories — `nav_order: 4`
6. CV — `nav_order: 5`
7. Teaching — `nav_order: 6`
8. People — `nav_order: 7`
9. Submenus — `nav_order: 8`

To hide a page, change `nav: true` to `nav: false`. Do not delete its file unless you also want its URL to disappear.

The dropdown is controlled by `_pages/submenus.md`:

```yaml
dropdown: true
children:
  - title: bookshelf
    permalink: /books/
  - title: blog
    permalink: /blog/
```

Every child `permalink` must match a real page. Otherwise visitors will see a 404 page.

## 13. Run and test on Windows

Open PowerShell and run:

```powershell
cd D:\DP_sir_portfolio\dipanjyoti

& 'C:\ProgramData\rvm\envs\ruby-3.3.5\bin\bundle.bat' _4.0.6_ exec jekyll serve --livereload --config _config.yml,_config.windows.yml
```

Open this address in a browser:

```text
http://127.0.0.1:4000/dipanjyoti/
```

Jekyll watches the files. After saving a file, wait a few seconds and refresh the browser. Press `Ctrl+C` in PowerShell to stop the server.

### Run a build-only test

This checks that Jekyll can build everything without starting a server:

```powershell
& 'C:\ProgramData\rvm\envs\ruby-3.3.5\bin\bundle.bat' _4.0.6_ exec jekyll build --config _config.yml,_config.windows.yml
```

If the command finishes with `done`, the build succeeded. The Windows override turns off local responsive-image conversion because Windows has another program named `convert`. GitHub Actions uses the main configuration and generates the optimized images normally.

## 14. Save changes with Git

From the repository folder, inspect the changes:

```powershell
git status
git diff
```

Save them in a commit:

```powershell
git add .
git commit -m "Update portfolio information"
```

Upload them:

```powershell
git push origin main
```

The GitHub account used for the push must have write permission to the repository.

## 15. Let GitHub publish the website

After pushing to `main`:

1. Open the repository on GitHub.
2. Click the **Actions** tab.
3. Open the newest deployment run.
4. Wait for every build step to become green.
5. Open `https://dipanjyoti.github.io/dipanjyoti/`.
6. Perform a hard refresh if the browser still shows an older version (`Ctrl+F5` on Windows).

Do not manually edit the `gh-pages` branch. The workflow creates it from the files on `main`.

## 16. Simple final checklist

Before pushing, check all of these:

- The home page shows the correct name, photograph, biography, and appointments.
- Every navigation item opens a real page.
- Unfinished pages visibly say **To be updated.**
- The CV page contains the newest positions, education, interests, and memberships.
- The CV PDF button downloads the newest PDF.
- Publication titles, years, links, and author names are correct.
- Project and repository links open the intended GitHub pages.
- Email and social icons point to the correct accounts.
- The local Jekyll build finishes successfully.
- The GitHub Actions deployment is green after pushing.

## 17. Common mistakes and easy fixes

### The website has no styling

Make sure `_config.yml` still contains:

```yaml
url: https://dipanjyoti.github.io
baseurl: /dipanjyoti
```

### A page does not appear in the navigation

Check that its front matter contains `nav: true` and a unique `nav_order`.

### A page gives a 404 error

Check that the link exactly matches the page's `permalink`, including the leading and trailing `/`.

### The build reports a YAML error

Look at the line named in the error. Common causes are a missing colon, uneven indentation, a tab character, or text containing a colon that needs quotation marks.

### The old website is still visible after deployment

Wait for the GitHub Actions deployment to finish, then use `Ctrl+F5` or open the site in a private browser window.

### `git push` says permission denied

Sign in to GitHub with an account that owns the repository or has been added as a collaborator. The website files can still be edited and tested locally without push access.
