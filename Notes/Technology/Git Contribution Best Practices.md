# Git Contribution Best Practices

### Preparation

1. **Understand the Project Goals**: Familiarize yourself with the project’s mission, goals, and current issues by reading its README, `CONTRIBUTING.md`, and other documentation.
2. **Review Open Issues**: Look through open issues to find tasks that match your skill level or interest. Beginner-friendly issues are often labeled (e.g., `good first issue`).
3. **Follow the Project's Style Guidelines**: Review any style or coding guidelines provided by the project and adhere to them.

---

### Forking and Cloning

1. **Always Fork the Repo**: Avoid working directly on the main repository. Fork the repo to your GitHub account and clone it locally.
2. **Add and Verify the Upstream Repository**: Set the original repo as the upstream and fetch updates regularly to keep your fork synced.

---

### Working on Your Contribution

1. **Create a New Branch**: Always create a new branch for each contribution (e.g., `fix-bug-123` or `add-feature-x`). Never work on the `main` branch.
2. **Make Small, Focused Changes**: Avoid bundling multiple features or fixes into a single PR. Keep each PR focused and limited in scope.
3. **Write Meaningful Commit Messages**: Use clear, descriptive commit messages that explain the _why_ and _what_ of your changes (e.g., `Fix login button alignment on mobile`).

---

### Testing and Linting

1. **Run Existing Tests**: Before making changes, run the project's tests to ensure the environment is correctly set up.
2. **Write New Tests**: Add unit tests or integration tests for your changes, if applicable.
3. **Lint Your Code**: Use the project’s linting tools to ensure your code adheres to style guidelines.

---

### Syncing Your Fork

1. **Fetch and Rebase Regularly**: Before pushing or creating a PR, fetch the latest changes from `upstream` and rebase your branch to avoid conflicts.
2. **Resolve Conflicts Gracefully**: If conflicts arise during rebasing, carefully resolve them and double-check the changes.

---

### Creating a Pull Request

1. **Create a Draft PR**: If your work is incomplete but you’d like feedback, create a draft PR on GitHub.
2. **Provide a Detailed Description**: Write a clear PR title and description. Explain _what_ your changes do, _why_ they’re necessary, and link any related issues (e.g., `Fixes #123`).
3. **Follow PR Templates**: Many projects provide templates for PRs. Use them to structure your submission.

---

### Responding to Feedback

1. **Be Open to Feedback**: Accept constructive criticism and be willing to make changes.
2. **Address Feedback Promptly**: Update your branch to incorporate requested changes and push the updates to your fork.
3. **Communicate Clearly**: If you’re unsure about feedback, ask questions to clarify the reviewer’s expectations.

---

### General Etiquette

1. **Be Respectful**: Always communicate politely with maintainers and contributors.
2. **Contribute Documentation**: If you find missing or outdated documentation, consider improving it.
3. **Avoid Unnecessary Changes**: Do not submit changes unrelated to the issue you’re addressing, like reformatting unrelated code.

---

### Technical Best Practices

1. **Use Descriptive Branch Names**: Use branch names that describe your work clearly (e.g., `fix-typo-in-readme` or `add-user-auth`).
2. **Avoid Force-Pushing to Upstream**: Use force-push (`--force-with-lease`) only on your PR branch in your fork, and never on the upstream repo.
3. **Test Across Environments**: Test your changes across all environments supported by the project (e.g., Windows, macOS, Linux).
4. **Squash Commits**: Before finalizing your PR, squash commits to clean up your commit history (if required by the project).

```shell
git rebase -i HEAD~<number-of-commits>
```

---

### After the Contribution

1. **Follow Up on Your PR**: Monitor the status of your PR and respond to comments in a timely manner.
2. **Celebrate Merges**: If your PR is merged, celebrate your contribution and thank the maintainers!
3. **Clean Up Branches**: Delete your local and remote branches after your PR is merged to keep your repo tidy.

---

### Ongoing Contributions

1. **Stay Active**: Continue contributing to the project to build trust and familiarity with maintainers.
2. **Participate in Discussions**: Engage in issue discussions or community forums to help others and learn more.
3. **Be Patient**: Understand that maintainers are often volunteers, and PR reviews may take time.

---

### What to Avoid

1. **Avoid Premature PRs**: Don’t open a PR for incomplete work unless it's a draft and you're seeking feedback.
2. **Avoid Overwriting Maintainer Code**: Respect existing work and discuss significant changes before implementing them.
3. **Don’t Assume Ownership**: Be mindful that the project belongs to the community, not just to you.
