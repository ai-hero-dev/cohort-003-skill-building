# Setting Up Our Repo For GitHub Issues

Ralph needs a GitHub repository with issues enabled to work as your backlog. The challenge is that you're sharing the course repo with other students, so you can't push issues there.

The solution is to create a fork of the course repository on your local machine, then push it to a new private GitHub repository just for your Ralph exercises.

## Steps To Complete

### Create A Local Copy

- [ ] Navigate to the parent directory of your cloned course repo

Use `cd ..` to go up one level from wherever you cloned the course repository.

- [ ] Copy the entire course repository to a new directory

Copy the repo with a new name using `cp -r`:

```bash
cp -r cohort-003-project cohort-003-project-fork
```

This creates a complete copy including all git history and `node_modules`.

- [ ] Open the fork directory

Navigate into your new directory:

```bash
cd cohort-003-project-fork
```

### Disconnect From The Original Repo

- [ ] Remove the original git configuration

Delete the `.git` directory to disconnect from the original repository:

```bash
rm -rf .git
```

- [ ] Initialize a new git repository

Create a fresh git repository in this directory:

```bash
git init
```

- [ ] Create an initial commit

Stage all files and commit them:

```bash
git add .
git commit -m "initial"
```

### Set Up GitHub CLI

- [ ] Install the GitHub CLI

Visit [GitHub CLI](https://cli.github.com/) and follow the installation instructions for your operating system.

- [ ] Authenticate with GitHub

Log in to your GitHub account using the CLI:

```bash
gh auth login
```

Follow the prompts to authenticate. You'll be asked to choose between HTTPS or SSH, and whether to authenticate with a web browser or a personal access token.

### Push To A New GitHub Repository

- [ ] Create a new private repository on GitHub

Use the GitHub CLI to create a new private repo from your local code:

```bash
gh repo create --private --source=.
```

- [ ] Push your code to the new repository

Connect your local repository to the remote and push to the main branch:

```bash
git push --set-upstream origin main
```

### Verify Your Setup

- [ ] Visit your new repository on GitHub

Navigate to your GitHub account and find the new repository you just created.

- [ ] Confirm the code is there

You should see all your course project files in the repository.

- [ ] Confirm the repository is private

Check that the repository settings show it as private.

Once you've completed these steps, you have a dedicated GitHub repository ready for Ralph to use as a backlog. If you encounter any issues during setup, ask for help in Discord.