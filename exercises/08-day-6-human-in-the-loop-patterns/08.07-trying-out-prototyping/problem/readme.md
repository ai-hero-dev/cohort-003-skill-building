# Trying Out Prototyping

## Introduction

Our research into the live presence indicator is solid in theory, but we need to see it actually working before we commit to a full implementation.

Prototyping is your chance to apply your taste to design and catch bugs early. It's much cheaper to iterate on a throwaway version than to discover problems after you've already built the feature into the main app.

The prototype will live on a dev-only route, invisible to users, and will produce reusable assets that the implementation agent can drop directly into the real codebase.

## Steps To Complete

- [ ] Prepare your `/do-work` prompt with the research

Start with the `/do-work` skill. Include the `@plans/live-presence-indicator.md` research file so Claude has all the context it needs.

```
/do-work @plans/live-presence-indicator.md I want to build a prototype of the research here. I want this on a throwaway route that is only visible to developers. I want to create a local asset that the agent that ends up implementing this in the real app can actually use.
```

- [ ] Run the prompt and let Claude build the prototype

Claude will explore your codebase, install dependencies, and create the necessary files. This typically includes an auth endpoint, a dev route, and route registration.

- [ ] Sign up for [Ably](https://ably.com/)

You'll need a free Ably account to power the real-time presence updates. Create an app on the Ably dashboard and grab your API key.

- [ ] Add your Ably API key to your `.env`

Once you have your key, add it to your environment:

```
ABLY_API_KEY=your-key-here
```

- [ ] Test the prototype locally

Run `pnpm dev` and navigate to `/dev/presence`. Open a second tab and switch users (using the dev UI). You should see real-time presence updates between tabs.

- [ ] Document what you observe

Write down what works, what feels awkward, and any bugs you find. If you hit issues, head to the [Discord](https://aihero.dev/discord) to ask for help.

- [ ] Review the reusable assets

Claude will have created components and functions that the implementation agent can import or copy directly into the real feature. Make note of these so you can reference them in the implementation phase.