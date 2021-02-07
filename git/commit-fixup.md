# Create fix commits
- Use `git commit --fixup <commit-sha>` to mark this commit as a fix to the specified commit
- Proper way of doing "fix" or "follow up" commits
## Usage
- Stage your fix using `git add`
- Commit the fix using `git commit --fixup`

```shell
git commit --fixup 14b3fdf452bff00567b5cb2f459ff84cb9fe81b6
```

## Notes
- To keep the branch clean, use `git rebase -i --autosquash` to auto merge this fixup commit with the associated commit

## Experiences
- In the past, whenever I do follow up commits (usually when I forgot to include a file, or there's just a minor change that I want to add up to my previous commit), I usually do a normal commit with this message format:
```
Commit Message: Follow up commit for <commit-sha>
```

## Resources
- https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---fixupltcommitgt
- https://fle.github.io/git-tip-keep-your-branch-clean-with-fixup-and-autosquash.html
