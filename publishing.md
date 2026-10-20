# Publishing

The book is served by GitHub Pages at <https://trustworthyresear.ch>, from the `gh-pages` branch of this repository. The custom domain comes from `CNAME`, which `_quarto.yml` copies into the rendered site. The old Quarto Pub site (ianhussey.quarto.pub) is no longer used, so there is no `_publish.yml`: publishing to GitHub Pages does not need one.

Work on the `dev` branch. Commit and push the source first, then publish:

```
cd ~/git/trustworthiness-assessment-and-forensic-meta-science
quarto publish gh-pages
```

This renders the whole book, which runs every chapter's R code, so the packages it uses must be installed locally. If the book has just been rendered in full with `quarto render`, publish that render without rendering again:

```
quarto publish gh-pages --no-render
```

GitHub Pages takes a few minutes to deploy, and browsers may cache the old pages.

## Preview

```
quarto preview
```

## The webR calculators

The calculators in chapter 10 run R in the reader's browser. Most install their packages from the webR repository, but {recalc} is not available there, so they download its R code from GitHub at a fixed commit, set by `recalcCommit` in `chapters/10_recalculation_methods.qmd`. After changing {recalc}, push it, then update `recalcCommit` to the new commit and republish. The calculators do not pick up changes to {recalc} until then.
