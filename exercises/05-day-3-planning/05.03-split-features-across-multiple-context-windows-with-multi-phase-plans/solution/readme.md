The AI has already created a plan in `plans/instructor-analytics-dashboard.md`. What's immediately striking is how quickly it generates output and eagerly produces an asset without asking many questions first:

![Showing the AI creating the asset](https://res.cloudinary.com/total-typescript/image/upload/v1773316927/ai-hero-images/fzeojsmkthxmozj0yfdf.png)

With the `/write-a-prd` skill, we had a rich conversation with the LLM. Here, it's just producing something immediately. Let's see how good it is.

## Examining the Plan Structure

The plan is saved inside the `plans` directory. Claude has created four phases:

1. **Analytics Service + Tests** - the backend architecture, creating the analytics service separately first
2. **Shared Dashboard Component + Recharts** - installing recharts and creating a shared dashboard component
3. **Instructor Analytics Route** - using that UI in a route and creating the admin analytics route
4. **Admin Analytics Route + Users Page Link** - adding the user's page link

This is a horizontal approach: each phase tackles a complete vertical slice of functionality.

![Showing four phases](https://res.cloudinary.com/total-typescript/image/upload/v1773316927/ai-hero-images/faxp8vsfzbwt8igrj4v6.png)

## The Problem with Too Much Detail

Inside each phase, Claude has mapped out all the individual steps. This looks like a pure implementation guide or user manual.

```md
## Phase 1: Analytics Service + Tests

Build the core data layer behind a simple, testable interface. No UI work yet.

### Steps

1. **Create `app/services/analyticsService.ts`** with a single main function:
   - `getInstructorAnalytics(opts: { instructorId: number; period: "7d" | "30d" | "12m" | "all" })` → returns `{ summary, timeSeries, courses }`
   - `summary`: `{ totalRevenue: number; totalEnrollments: number; averageRating: number | null; ratingCount: number }`
     ...
```

Here's the issue: as a developer, I know you can't get all the designs right before you actually implement.

Phase 1 works well because you're just making changes to the existing codebase. But look at Phase 3:

```md
## Phase 3: Instructor Analytics Route

Wire up the instructor-facing route.

### Steps

1. **Create route file `app/routes/instructor.analytics.tsx`** (maps to `/instructor/analytics`):
   - **Loader:**
     - `getCurrentUserId(request)` → redirect to `/login` if null
     - `getUserById(userId)` → 403 if not `UserRole.Instructor`
```

The plan references functions that might not even exist by the time you reach implementation. If during Phase 1 you decide to implement things differently, these specific functions go stale very quickly.

## What Works Well

The acceptance criteria are excellent. They make it clear what success looks like for each phase:

![Acceptance criteria](https://res.cloudinary.com/total-typescript/image/upload/v1773316930/ai-hero-images/emdnd6semmsrywudooi5.png)

However, the plan doesn't reference the user stories from the PRD. Those user stories were carefully considered, and linking them back to the plan would maintain that connection to the "why".

## Sizing and Layering

Looking back at the full plan, the task sizing is reasonable:

| Phase   | Size   | Notes                                                                                                                            |
| ------- | ------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Phase 1 | Medium | Analytics service and tests might be harder than expected, but since we're only querying the database, it may be straightforward |
| Phase 2 | Medium | Building the dashboard component                                                                                                 |
| Phase 3 | Medium | Wiring up the instructor route                                                                                                   |
| Phase 4 | Small  | Admin route and link                                                                                                             |

None of these look too large. Phases 3 and 4 could potentially be condensed since they're similar work.

## The Naïve Plan Approach

So here's what we've got: a relatively naïve plan that does all its work in horizontal layers. We'll explain why that's problematic in the next few videos.

The plan is also too specific with implementation details. It names functions which might not exist by the time you reach later phases. However, it is fairly nicely sized, and the acceptance criteria are solid.

Hopefully you reached some of the same conclusions as me, and I'd love to hear your thoughts in [Discord](https://aihero.dev/discord) if you noticed anything different.
