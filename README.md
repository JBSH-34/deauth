# Deauth

## Development Setup

### Initial Settings

To begin, install the necessary packages using Yarn.

```bash
yarn install
```

After the installation is complete, you can start the development server.

```bash
yarn dev
```

Ensure to configure [husky](#husky) before committing your code. **Do not** attempt to resolve dependency errors without notifying your team.

---

### GitHub Usage Guidelines

#### Commit Message Structure

Commit messages should follow this structure.

```
Type: Subject

Body

Footer
```

#### Commit Types

Write the commit type followed by a colon and a space, then the subject.

```
Type: Subject
```

| Tag Name         | Description                                                               |
| ---------------- | ------------------------------------------------------------------------- |
| Feat             | Adds a new feature                                                        |
| Fix              | Fixes a bug                                                               |
| Design           | Changes in UI, modifies CSS                                               |
| !BREAKING CHANGE | Introduces a major change                                                 |
| !HOTFIX          | Fixes a critical bug in a live deployment                                 |
| Style            | Code formatting, linting, no logic change                                 |
| Refactor         | Code restructuring without changing behavior                              |
| Comment          | Adds or updates comments                                                  |
| Docs             | Documentation updates                                                     |
| Test             | Adds tests, no production code change                                     |
| Chore            | Other updates; build scripts, package manager                             |
| Rename           | Renames or moves files, no logic change                                   |
| Remove           | Deletes files                                                             |
| Update           | Enhances functionality that was already working properly                  |
| Add              | Introduces new code, components, or files                                 |
| Remove           | Deletes files                                                             |
| Simpify          | Simplifies code, weaker than a refactor, focuses on clarity               |
| Improve          | Enhances compatibility, test coverage, performance, validation, or access |
| Implement        | Brings a new implementation, bigger than a simple addition                |
| Correct          | Corrects grammatical, typing, or naming errors                            |
| Prevent          | Adds changes aimed at preventing future issues or errors                  |

Additional information can be included in parentheses.

```
Feat(navigation)
Fix(db)
```

#### Subject

Begin the subject with a capital letter and limit it to 50 characters. Do not use punctuation or special characters, and start with a verb in the imperative mood for clarity.

```
Added file --> Add License file
Fixed code --> Fix #1234 button not working.
Update .gitignore --> Add .idea folder to .gitignore
```

#### Body

Explain **the reason for the changes** in the code in under 70 characters, detailed and clearly.

#### Footer

Only specify the issue ID in the format `Type: #IssueNumber` if applicable. Use commas to separate multiple issues.

```
Fixes: #45 Related to: #34, #23
Resolves: #123
Ref: #456
Related to: #48, #45
```

---

### husky

After running yarn install, husky will automatically configure its folder via postinstall. Replace the contents of the pre-commit and pre-push files with the following scripts.

#### pre-commit

```bash
#!/usr/bin/env sh
. "${0%/*}/h"

yarn prettier --cache --write .
git add .
```

#### pre-push

```bash
#!/usr/bin/env sh
. "${0%/*}/h"

yarn lint-staged
yarn tsc -p tsconfig.json --noEmit
```
