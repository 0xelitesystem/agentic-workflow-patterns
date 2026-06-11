# Tasks not to delegate

## What doesn't belong to an agent

These are tasks where the cost of an AI failure exceeds the benefit of AI speed.

### Cryptographic implementations

Don't ask agents to implement crypto. Use established libraries. Even reviewing crypto code requires expertise the agent can't validate.

### Security-critical code without independent review

Auth flows, payment processing, secret handling. Agents can write these, but you need a security-trained human to review what they wrote, and the review has to be more careful than usual.

### Architecture decisions

"Should we use a queue or a database table for this work?" is a tradeoff with long-term consequences the agent can't reason about (your team's familiarity with each, your scaling profile, your deployment constraints). Make the decision yourself; let the agent implement it.

### Production debugging under pressure

When the system is on fire, the loop "agent proposes fix, you verify, fix doesn't work, agent proposes another" is too slow. Diagnose yourself, fix yourself. Use the agent later for the postmortem.

### Anything you don't understand the success criteria for

If you can't write a verification, you can't tell if the agent did it right. Don't delegate. Either learn enough to verify, or don't do this task with AI.

### Tasks with long, asymmetric consequences

Migrations on production data. Force-push to shared branches. Public communications. Anything with a "you can't take it back" quality.

### Code where you'd reject a junior dev's PR without senior review

If you'd require senior review from a human, you should require careful review of the agent's version. The reduction in dev time doesn't reduce review needs.

## What this list isn't

This isn't "don't use AI for hard things." It's "for these specific tasks, the AI savings aren't worth the risk."

The flip side: most tasks aren't on this list. Boilerplate, simple bugs, refactors, tests, glue code, doc generation, agents are great at these. Save your skepticism for where it matters.
