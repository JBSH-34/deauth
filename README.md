# Deauth

## dev

### husky

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
