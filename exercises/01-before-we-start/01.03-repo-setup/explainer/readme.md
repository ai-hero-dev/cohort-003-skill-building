Before you start building, you need to get the course project running locally. This involves cloning the repository, installing Node.js and `pnpm`, seeding the database, and setting up Claude Code.

The good news is that the setup is straightforward - just follow the steps below in order.

## Steps To Complete

### Clone the Repository

- [ ] Clone the [project repo](https://github.com/ai-hero-dev/cohort-003-project) to your local machine

```bash
git clone https://github.com/ai-hero-dev/cohort-003-project.git
```


### Install Node.js

- [ ] Download and install Node.js from https://nodejs.org/en/download

Choose either version 22 or version 24 - both will work fine.

![Node.js download page showing version selection and platform options](https://res.cloudinary.com/total-typescript/image/upload/v1773399618/ai-hero-images/oif80orpuicljrevqjmw.png)

Select the installer for your operating system and follow the installation instructions.

- [ ] Verify Node.js is installed by running the following in your terminal

```bash
node -v
```

You should see a version number printed back.


### Set Up the Package Manager

- [ ] Enable `pnpm` by running this command in your terminal

```bash
corepack enable
```

This installs `pnpm`, the package manager used by this project.

- [ ] Verify `pnpm` is installed by running

```bash
pnpm -v
```

You should see a version number printed back.


### Install Dependencies

- [ ] Install the project dependencies

```bash
pnpm install
```

This downloads all the required packages from the NPM registry into your `node_modules` folder.


### Seed the Database

- [ ] Start the development server

```bash
pnpm dev
```

If you see an error like "No such table courses", that's expected.

![Terminal showing 'No such table courses' error](https://res.cloudinary.com/total-typescript/image/upload/v1773399619/ai-hero-images/zrrtjwk6npduztgvff0m.png)

Stop the server by pressing `CTRL-C`.

- [ ] Seed the database with dummy data

```bash
pnpm db:seed
```

This creates the database tables and populates them with sample data - users, courses, quizzes, enrollments, and more.

![Terminal output showing database seeding with created tables and dummy data](https://res.cloudinary.com/total-typescript/image/upload/v1773399620/ai-hero-images/hjlthf1jc3cnk9t8esfr.png)

- [ ] Start the development server again

```bash
pnpm dev
```

The development server should now start successfully and run on `localhost:5173` or similar.


### Install Claude Code

- [ ] Stop the development server by pressing `CTRL-C`

- [ ] Install Claude Code

Visit the [Claude Code setup docs](https://code.claude.com/docs/en/setup) and follow the installation instructions for your editor.

- [ ] Run Claude Code in your terminal

```bash
claude
```

This should open Claude Code.

![Claude Code interface open in the terminal](https://res.cloudinary.com/total-typescript/image/upload/v1773399620/ai-hero-images/fqmjsvsr5vkdqsltiwoq.png)

You may need to log in with your Anthropic subscription or API key. A subscription is recommended as it's more cost-effective than an API key.

- [ ] You're ready to start the course!

If you hit any issues during setup, head to the [AI Hero Discord](https://aihero.dev/discord) and ask for help.