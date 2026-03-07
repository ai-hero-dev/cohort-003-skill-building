# Red-Green-Refactor

You've built a `/do-work` skill that helps your agent plan and execute features. But right now, it just works through the plan step by step without any structured feedback loop.

Test-driven development (TDD) is a powerful feedback loop. Instead of implementing a whole feature and hoping it works, you write a small failing test first, make it pass, then refactor. This keeps you moving fast and confident.

You're going to update your `/do-work` skill to encourage TDD for backend code using the red-green-refactor pattern. Then you'll test it on a real feature.

## Steps To Complete

### Update the /do-work Skill

- [ ] Open a fresh Claude Code instance and use the `/write-a-skill` command

Ask it to add red-green-refactor guidance into the implementation step of your `/do-work` skill.

- [ ] Make sure the skill encourages one test at a time in a tracer-bullet style

Each test should target a thin vertical slice of behavior: one API endpoint returning one shape of data, one service method handling one case. The agent should write one test, make it pass, then move to the next test.

- [ ] Add a stipulation that this applies **only to backend code**, not frontend code

The reason is that your test suite only works for backend code right now. You don't have a frontend-facing test setup yet. Frontend code changes too fluidly during development for test-first to be practical anyway.

Your updated skill should explain the red-green-refactor loop clearly:

1. Write a single failing test for the smallest vertical slice of behavior
2. Run the test, confirm it fails (red)
3. Write the minimum code to make it pass (green)
4. Refactor if needed while keeping tests green
5. Repeat for the next slice of behavior

### Test the Skill on a Real Feature

- [ ] Navigate to the `Coupon Redemption Notifications` PRD and plan in your codebase

You should have both the PRD and the multi-phase plan file ready.

- [ ] Open a fresh Claude Code instance and pass in both files

Use the `/do-work` command with the PRD and plan attached, then run `Do Phase 1`.

- [ ] Watch Claude Code execute the red-green-refactor loop

This is the satisfying part. You should see the agent:

- Write a failing test for notification creation on coupon redemption
- Run the test and watch it fail
- Implement the minimum code to make it pass
- Write the next test
- Repeat until the feature is complete
- Run the full test suite to validate everything

The agent should create in-app notifications for team admins when someone redeems a coupon belonging to their team, showing the redeemer's name, course title, and remaining seat counts.

- [ ] Verify all tests pass and typecheck is clean

Once the feature is complete, make sure the test suite passes and there are no TypeScript errors.

### QA: Validating Your Feature

- [ ] Log in as a team admin and purchase course seats

Navigate to a course and buy multiple seats for your team. You'll be redirected to your team management section where you can distribute coupon codes.

- [ ] Copy a coupon code and log out

Generate at least one coupon code and copy it to your clipboard.

- [ ] Sign up as a new user

Create a fresh account with a different email address.

- [ ] Redeem the coupon code

Navigate to the coupon redemption URL (or manually enter the code) and enroll in the course.

- [ ] Log back in as the team admin and check for notifications

You should see a notification saying the new user redeemed a coupon for the course, with the remaining seat count displayed.

- [ ] (Optional) Test with multiple team admins

Add a second admin to your team, have someone redeem another coupon, and verify that both admins receive the notification.

### What to Watch For

The agent may write multiple tests upfront instead of strictly following the tracer-bullet approach. This is a sign it's confident about the implementation, but if you want stricter adherence to one test at a time, you can refine your skill's guidance to emphasize that pattern more strongly.

All tests should pass at the end, and the feature should work end-to-end without manual fixes needed. This is the beauty of TDD: you get confidence that the implementation is solid.
