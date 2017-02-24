# Git commit hooks for rust projects.

## Usage

1. Copy the update-docs/post-commit file into your .git/hooks/
  and make it executable
```bash
# git checkout master
cp update-docs/post-commit .git/hooks/
chmod +x .git/hooks/post-commit
```

2. Develop your project, add crates to Cargo.toml and so on. After each commit on the `master` branch,
  the documentaion is rebuild.
  If you're ready push the `gh-pages` branch to publish the new documentation.
```bash
git checkout gh-pages
git push
```

3. Final visit your new website under '`http(s)://<username>.github.io/<projectname>/<crate_name>/index.html`'
e.g.https://zzeroo.github.io/rust-git-hooks/rust_git_hooks/index.html
