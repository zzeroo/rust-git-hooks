# Git commit hooks for rust projects.

[Homepage](https://zzeroo.github.io/rust-git-hooks/) | [Documentation](https://zzeroo.github.io/rust-git-hooks/rust_git_hooks/index.html)

## Usage

1. Copy the update-docs/post-commit file into your .git/hooks/
  and make it executable
```bash
# git checkout master
cp update-docs/post-commit .git/hooks/
chmod +x .git/hooks/post-commit
```

2. Develop your project, add crates to Cargo.toml and so on.
  After each commit on the `master` branch, the documentaion is rebuild by the `post-commit` hook script.
  If you're ready push the `gh-pages` branch to publish the new documentation.
```bash
git push origin gh-pages
```

3. Final visit your new website under '`http(s)://<username>.github.io/<projectname>/<crate_name>/index.html`'
e.g.[https://zzeroo.github.io/rust-git-hooks/rust_git_hooks/index.html](https://zzeroo.github.io/rust-git-hooks/rust_git_hooks/index.html)

## Additional

If you want a "homepage" for your project, you need a `index.html` in the root of the `gh-pages` branch.

I prefer to generate a `index.html` from the project `README.md`. Use a markdown to html tool like [pandoc](http://pandoc.org/) for that, or write your own `index.html` if you like.

```bash
git checkout gh-pages
git checkout master README.md
pandoc --self-contained --highlight-style=tango -s -f markdown -t html5 -o index.html README.md
git add index.html
git reset HEAD README.md
rm README.md
git commit -a -m "Generate index.html from README.md"
git push
```

Now your project has a nice looking homepage under the URL `http(s)://<username>.github.io/<projectname>`.

Repeat these steps if you change the README.md.
