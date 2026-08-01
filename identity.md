# identity: voice anchors

The writing discipline behind every abukix artifact. These rules are the brand pillar; every `/root` file, every `basecamp` module README, every blog post, every commit message is authored against them.

**Status:** v0, the essentials. v1 lands in the `/root` Arc 5 Capstone period.

## The 9 voice anchors

Every anchor solves a specific failure mode that shows up in technical writing at scale. Don't skip the "Why": the rules only survive if the failure mode is understood.

### 1. Direct, opinionated, no fluff

- No hedge-words: **no** "might be", "perhaps", "you may want to", "somewhat", "could potentially".
- If you're uncertain, say so with a real reason ("I haven't operated this at scale"). Don't hide it in soft language.

**Why:** hedge-words are anti-signal. They train the reader to skim past the actual argument.

### 2. Pattern-first

- Always name the underlying pattern before naming the tool.
- "Control loops" before "Kubernetes." "Idempotency" before "Retry-After." "Composition contract" before "Crossplane XRD."

**Why:** tools churn every ~5 years. Patterns compound over a career. Writing tool-first ages badly.

### 3. No marketing language

- **Not allowed:** "revolutionary", "game-changing", "10x", "cutting-edge", "AI-powered".
- Describe what a thing *does*, not how impressive it is.

**Why:** every marketing word substitutes for a specific claim. The reader loses information, and the writer looks unserious.

### 4. No emojis

- No emojis in authored prose. Ever, unless a user (or reader) explicitly asks for them.
- The rocket-themed `bootstrap.sh` script is an exception — theming a runtime UI is not the same as authoring documentation.

**Why:** emojis feel like brand-warmth signals but they degrade the perception of technical rigor. Serious documentation doesn't wear costumes.

### 5. Trade-offs explicit

- Tables when there are more than two options being compared.
- Prose for two.
- Never leave a trade-off implicit.

**Why:** the reader is trying to decide. A decision without stated trade-offs is a recommendation without the reasoning, and the reader can't adapt it to their context.

### 6. Time-stamp the volatile bits

- Tool sections get a date ("Last verified: 2026-07 against Cilium 1.16").
- Pattern sections don't. They're timeless.

**Why:** stale tool advice damages trust in the whole document. Timestamps let the reader calibrate.

### 7. Investigation prompts, not recipes

- In curriculum context: phase docs guide the operator to investigate; they don't hand over a recipe.
- The reader is the one doing the work; the writer is the guide.

**Why:** copy-paste knowledge doesn't compound. The reader retains what they investigated themselves.

### 8. No false modesty, no overclaim

- A homelab K3s cluster is a homelab K3s cluster. Don't inflate it into "production-grade infrastructure."
- Equally: don't call five years of platform engineering "just tinkering."
- Pattern fluency is the claim. Scale is what it is.

**Why:** both directions of miscalibration erode trust. Honest scale-of-experience is the ground floor.

### 9. Honest about failure

- Postmortems are blameless and specific.
- Weekly logs admit what's stuck.
- Something didn't work? Say so, and say what you learned.

**Why:** the alternative is performative optimism, which is the fastest way to lose credibility with senior readers.

## Enforcement

Voice violations are caught by:
- The [`root-tutor` skill](https://github.com/abukix/root/tree/main/.claude/skills/root-tutor) in `/root`: refuses to write in a way that violates anchors 1, 3, 4.
- The [`pre-publish-check` skill](https://github.com/abukix/root/tree/main/.claude/skills/pre-publish-check) in `/root`: greps for hedge-words and marketing words heuristically.
- Reviewers: every PR checks against these anchors.

## Cross-references

- [`typography.md`](typography.md): how the voice is set (JetBrains Mono for code + wordmark, Inter Variable for body)
- [`colors.md`](colors.md): the family gradient (purple, pink, orange)
- [`wordmark/`](wordmark/): SVG files + rendering rules
