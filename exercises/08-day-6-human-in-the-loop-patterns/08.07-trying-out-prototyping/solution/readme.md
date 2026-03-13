The agent starts by exploring the codebase to understand the project structure, routing, and authentication patterns.

While the exploration runs, there's an important principle worth highlighting about the `/do-work` skill: it enables human-in-the-loop mini sprints that maintain code quality in our prototype from the very beginning.

Even in simple prototype code, you should apply rigorous code standards. This includes:

- Writing proper feedback loops
- Applying TDD practices
- Following your codebase conventions

Why? When the implementation agent copies this prototype code into the real application, they'll be copying genuinely production-ready code. This saves time and prevents quality regressions later.

## Creating the Prototype Files

Once the exploration completes, the agent feels confident enough to start adding files without extensive planning. The agent creates three key files:

1. **`app/routes/api.ably-auth.ts`** - A token auth endpoint that validates the user session and creates a signed Ably token request using the server-side API key.

2. **`app/routes/dev.presence.tsx`** - A dev-only prototype page at `/dev/presence` containing:
   - `PresenceIndicator` - A reusable, exported component showing "Matt, Sarah, and 2 others are here" with a pulsing green indicator
   - `PresencePill` - Display logic for the presence text formatting
   - `createAblyClient` - An exported factory function for creating the Ably Realtime client
   - Demo UI with channel switcher, connection status, and debug view
   - Production guard that returns a 404 in production

3. **`app/routes.ts`** - Route registrations for both the auth endpoint and dev page

![The agent running typecheck and tests, then committing the changes](https://res.cloudinary.com/total-typescript/image/upload/v1773388425/ai-hero-images/skv47dkxc7vys6twwjym.png)

The agent does something particularly nice here: it makes the prototype components reusable and exports them from the prototype module. This design allows the components to be dropped immediately into the real app without rework.

The typecheck passes, all 396 tests pass, and everything gets committed with a clean git history.

## Getting Your Ably API Key

Before testing the prototype, you need an Ably API key. Here's how to acquire one with the correct scopes:

| Step                | Action                                                                                                                |
| ------------------- | --------------------------------------------------------------------------------------------------------------------- |
| 1. Create account   | Go to [ably.com](https://ably.com/) and sign up (free tier supports 6M messages/month and 200 concurrent connections) |
| 2. Create app       | Click "Create New App", name it (e.g., `cadence-dev`), and select the Free plan                                       |
| 3. Get the API key  | Once created, go to the "API Keys" tab in the left sidebar. A default root key is already created                     |
| 4. Set capabilities | Ensure these are enabled: `subscribe`, `publish`, `presence`, `presence-subscribe`                                    |
| 5. Copy the key     | The key looks like: `xVLyHw.xxxxxx:xxxxxxxxxxxx`                                                                      |
| 6. Add to `.env`    | `ABLY_API_KEY=xVLyHw.xxxxxx:xxxxxxxxxxxx`                                                                             |

The key capabilities you need are:

- **`subscribe`** - Client receives presence events
- **`publish`** - Bundled with other capabilities by Ably
- **`presence`** - Enter/leave the presence set
- **`presence-subscribe`** - Receive others' presence events (this is the critical one that's easy to miss)

If you use the default root key, all of these are already enabled. Creating a more scoped key is optional but better practice.

## Testing the Prototype

Once you have your API key set in `.env`, you can test the live presence functionality:

```txt
pnpm dev
```

Then navigate to `/dev/presence` and:

1. Open the page in your browser
2. Open a second browser tab (or use an incognito tab to avoid shared sessions)
3. Use the DevUI to log in as a different user
4. Navigate to `/dev/presence` in the second tab

You should see real-time presence updates between tabs. When you log in as a second user, their name appears instantly on the first tab. When you log out, their presence disappears immediately.

![Two browser tabs showing live presence updates in real time as different users](https://res.cloudinary.com/total-typescript/image/upload/v1773388425/ai-hero-images/uwskyrz6exgifcgxkzhc.png)

## The Value of Prototyping

At this point, all the unknown unknowns are flushed out:

- You know the service works properly
- You know you can connect to it easily
- The rest of the implementation can be worked out asynchronously

This is the power of human-in-the-loop work. Rather than asking the AI to go off and build everything at once, then reviewing later, you sit and iterate with a prototype in a tight feedback loop. The tight feedback loop with the AI is incredibly beneficial and pays dividends when you move to the actual implementation phase.

The implementing agent can import directly from the prototype file:

```typescript
import { PresenceIndicator, createAblyClient } from "~/routes/dev.presence";
```

Or they can copy `PresenceIndicator`, `PresencePill`, and `createAblyClient` into their own module when integrating into the lesson page.

The prototype isn't throw-away code, it's production-ready code that validates your assumptions about an unknown unknown.
