# Dipanjyoti Paul — Academic Portfolio

Source for the academic portfolio of **Dr. Dipanjyoti Paul**, Assistant Professor at the University of Tsukuba and Visiting Scientist at The Ohio State University.

**Website:** [dipanjyoti.github.io/dipanjyoti](https://dipanjyoti.github.io/dipanjyoti/)

The site is built with [Jekyll](https://jekyllrb.com/) and [al-folio](https://github.com/alshedivat/al-folio), then deployed to the `gh-pages` branch by GitHub Actions.

## Research

Machine learning, computer vision, imageomics, explainable AI, AI in health, streaming data, real-time summarization, and foundation models.

## Local preview

```bash
bundle install
npm ci
bundle exec jekyll serve
```

Open <http://localhost:4000/dipanjyoti/>.

## Deployment

Pushes to `main` trigger `.github/workflows/deploy.yml`. In the repository settings, GitHub Pages must use **Deploy from a branch**, with the `gh-pages` branch and `/ (root)` folder selected.
