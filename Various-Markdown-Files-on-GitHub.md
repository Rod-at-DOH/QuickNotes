# Various Mardown files specific to GitHub

## The .github/pull_request_template.md file

### What `.github/pull_request_template.md` Is

**The** `.github/pull_request_template.md` **file is a Markdown template that GitHub automatically inserts into the body of every new pull request in your repository **
[GitHub Docs](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)

### How GitHub Uses It

When you create a new pull request, GitHub looks for a specially named file in your repository:

- Recommended location: `.github/pull_request_template.md `

- Other valid locations: pull_request_template.md in the repo root, or docs/pull_request_template.md 

If the file exists in `.github/`, GitHub will automatically use its contents as the default PR description. This means contributors don’t have to start from a blank page — they see a structured form with prompts and checklists 


### What You Can Put in It

The file can contain any Markdown you want, but best practices include:

- Description – a concise summary of what the PR does and why 

- Type of change – e.g., bug fix, feature, refactor, docs 

- Changes made – bullet list of specific modifications 

- How to test – steps for reviewers to verify the change 

- Checklist – items like “tests passed,” “docs updated,” “commit message follows guidelines” 

- Optional – links to related issues, screenshots, or code snippets 

Example snippet:

## The .github/release.yml file

```markdown
## Description
Briefly describe the purpose of this PR.

## Changes
- Added new API endpoint `/users`
- Updated `README.md` with usage instructions

## How to Test
1. Run `npm test`
2. Verify `/users` returns expected JSON

## Checklist
- [ ] Tests passed
- [ ] Documentation updated
```

### Why It’s Useful

- **Consistency** – ensures all PRs have required info 

- **Efficiency** – reduces back-and-forth by giving contributors a clear starting point 

- **Quality control** – reminds teams of review criteria and guidelines 

### How to Add It

1. Create the `.github` folder in your repo if it doesn’t exist.

2. Add a file named pull_request_template.md inside it.

3. Write your template content in Markdown.

4. Commit it to your default branch (e.g., main) 

## The `.github/release.md` file

### What is the .github/release.md file

A `.github/release.md` file is a Markdown document that can be used as a custom template or source for release notes in GitHub, often paired with automation tools or GitHub’s built‑in release note generation.

### How GitHub Uses It

GitHub itself does not natively require or automatically use a `.github/release.md` file for all releases. However, you can place a Markdown file in the `.github` directory — such as `release.md` — and use it in workflows, actions, or automation tools to generate or populate release notes when creating a [release](https://stackoverflow.com/questions/56798253/release-template-for-github).

For example:

- **Custom template**: You can store your preferred release notes format in `.github/release.md` and have an action (like `release-drafter` or a custom GitHub Action) read it to pre‑fill the “Describe this release” field when you draft a release 

- **Automation**: Some tools (e.g., `github-release-notes` / “gren”) can read a changelog or template file and automatically compile release notes from issues, commits, or tags 

- **Query‑parameter pre‑fill**: GitHub’s release form can be pre‑populated with content from a file via query parameters, which can point to `.github/release.md` 

### Relationship to .github/release.yml

GitHub also supports `.github/release.yml` for **automatically generated release notes** from tags, issues, and pull requests. This is different from `.github/release.md`:

- `.github/release.yml` → configuration for GitHub’s built‑in auto‑generation.

- `.github/release.md` → a Markdown file you can use as a template or source text for release notes, often combined with automation.

### Practical Example

If you have:

```markdown
.github/release.md
# Version 1.0.0
## Features
- Added new API endpoint
## Fixes
- Fixed login bug
```

And you use a GitHub Action to read this file, the action can insert its contents into the release description when you create a release.

### Key Points

- **Not mandatory**: GitHub doesn’t require it; it’s optional and project‑specific.

- **Template use**: Commonly used as a reusable template for release notes.

- **Automation**: Works with tools like `release-drafter`, `github-release-notes`, or custom scripts to auto‑populate releases.

- **Location**: Must be in the `.github` directory to be recognized by GitHub workflows or actions.

In short, `.github/release.md` is a customizable Markdown file for release notes that you can leverage with GitHub’s release automation or third‑party tools to streamline and standardize your release descriptions 
