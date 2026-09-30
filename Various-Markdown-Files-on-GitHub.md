# Various Mardown files specific to GitHub

## The .github/pull_request_template.md file

### What `.github/pull_request_template.md` Is

The .github/pull_request_template.md file is a Markdown template that GitHub automatically inserts into the body of every new pull request in your repository 
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

- Consistency – ensures all PRs have required info 
- Efficiency – reduces back-and-forth by giving contributors a clear starting point 
- Quality control – reminds teams of review criteria and guidelines 

### How to Add It

1. Create the `.github` folder in your repo if it doesn’t exist.
2. Add a file named pull_request_template.md inside it.
3. Write your template content in Markdown.
4. Commit it to your default branch (e.g., main) 
