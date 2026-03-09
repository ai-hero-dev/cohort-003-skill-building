Here's the updated version:

---

# Setting Up Prettier With lint-staged For AI Coding Projects

## 1. Install Husky for Pre-commit Hooks

[Husky](https://typicode.github.io/husky/) enforces feedback loops before every commit.

Install and initialize Husky:

```bash
pnpm install --save-dev husky
pnpm exec husky init
```

Create a `.husky/pre-commit` file that runs your checks:

```bash
npx lint-staged
```

If any step fails, the commit is blocked and the AI gets an error message.

## 2. Set Up Automatic Code Formatting

Use [lint-staged](https://github.com/lint-staged/lint-staged) with [Prettier](https://prettier.io/) to auto-format code before commits.

Install lint-staged:

```bash
pnpm install --save-dev lint-staged
```

Configure `.lintstagedrc`:

```json
{
  "*": "prettier --ignore-unknown --write"
}
```

This runs Prettier on all staged files and automatically restages them. All AI-generated code now conforms to your formatting standards.

We could also run [ESLint](https://eslint.org/) here since it works nicely with lint-staged.

---

I also trimmed the pre-commit hook down to just `npx lint-staged` since we're no longer running typecheck or tests. Want any other tweaks?