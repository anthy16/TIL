# Adding Value with Conventional Commits

I would never commit code with just an empty message ` ` - and yet I often find myself committing code with just as meaningless commit messages. Things like `fixed bug in component` or `implemented feature`. Sure, those are words. But they really are not explaining what that commit is doing.

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) adds a pretty bulletproof way of writing commit messages, that will at least convey some sort of meaning. The structure is as follows:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

The type explains what you're doing. Fixing a bug? Use _fix_. Adding a feature? Use _feat_. There's a couple of other types you can use, found at [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional). These are based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines);

The description field is what you're doing in said commit. The body can be used to detail this further.

Footers can provide context, e.g. if introducing a breaking change, you would use _BREAKING CHANGE: <description>_.

If you find that your code doesn't fit a single type, make multiple commits instead - one for each type.
