# Morphic Programming: A First Principles Manual for Agentic AI

**By Nicola Sahar**

---

## Table of Contents

- [Part 1: Introduction](#part-1-introduction)
  - [Why You Should Read This Manual](#why-you-should-read-this-manual)
  - [Who Am I?](#who-am-i)
  - [Why Am I Writing This?](#why-am-i-writing-this)
  - [How Is This Manual Structured?](#how-is-this-manual-structured)
  - [This Manual Is Free](#this-manual-is-free)
  - [A Few Disclaimers](#a-few-disclaimers)
- [Part 2: First Principles of Morphic Programming](#part-2-first-principles-of-morphic-programming)
  - [Principle 1: Morphability](#principle-1-morphability)
  - [Principle 2: Abstraction](#principle-2-abstraction)
  - [Principle 3: Recursion](#principle-3-recursion)
  - [Principle 4: Internal Consistency](#principle-4-internal-consistency)
  - [Principle 5: Reproducibility](#principle-5-reproducibility)
  - [Principle 6: Morphic Complexity](#principle-6-morphic-complexity)
  - [Principle 7: End-to-End Autonomy](#principle-7-end-to-end-autonomy)
  - [Principle 8: Token Efficiency (Experimental)](#principle-8-token-efficiency-experimental)
  - [Principle 9: Mutation and Exploration (Experimental)](#principle-9-mutation-and-exploration-experimental)
- [Part 3: System Design for Morphic Programming](#part-3-system-design-for-morphic-programming)
  - [Repository Structure](#repository-structure)
  - [Use CLI Agents](#use-cli-agents)
  - [Use Git](#use-git)
  - [Context Engineering](#context-engineering)
  - [A Note on Agent Orchestration](#a-note-on-agent-orchestration)
  - [A Note on IDEs and Models](#a-note-on-ides-and-models)
  - [A Note on Vibe Coding](#a-note-on-vibe-coding)
- [Part 4: Practical Tips and Psychology](#part-4-practical-tips-and-psychology)
  - [What Actually Matters](#what-actually-matters)
  - [What Does Not Matter](#what-does-not-matter)
  - [Psychological Tips](#psychological-tips)
  - [The Work Cycle](#the-work-cycle)
- [Part 5: Conclusion and Future Topics](#part-5-conclusion-and-future-topics)
  - [Parting Words](#parting-words)
  - [Future Topics](#future-topics)
  - [Get in Touch](#get-in-touch)
- [Appendix: Generic Commands Reference](#appendix-generic-commands-reference)

---

# Part 1: Introduction

## Why You Should Read This Manual

You should read this manual:

- **If you resonate with what Andrej Karpathy recently said** on Dec 26, 2025 on X ([source](https://x.com/karpathy/status/2004607146781278521)):

> "I've never felt this much behind as a programmer. The profession is being dramatically refactored as the bits contributed by the programmer are increasingly sparse and between. I have a sense that I could be 10X more powerful if I just properly string together what has become available over the last ~year and a failure to claim the boost feels decidedly like skill issue. There's a new programmable layer of abstraction to master (in addition to the usual layers below) involving agents, subagents, their prompts, contexts, memory, modes, permissions, tools, plugins, skills, hooks, MCP, LSP, slash commands, workflows, IDE integrations, and a need to build an all-encompassing mental model for strengths and pitfalls of fundamentally stochastic, fallible, unintelligible and changing entities suddenly intermingled with what used to be good old fashioned engineering. Clearly some powerful alien tool was handed around except it comes with no manual and everyone has to figure out how to hold it and operate it, while the resulting magnitude 9 earthquake is rocking the profession. Roll up your sleeves to not fall behind."

- If you feel like you aren't able to get the most out of these systems, and that you are massively under-leveraging them
- If you ultimately want AI to run much of the menial stuff in your life, or do more useful things for you
- If you have so many ideas but not enough time to implement them

---

## Who Am I?

- I founded and sold [Semantic Health](https://betakit.com/semantic-health-acquired-by-us-based-medical-documentation-firm-aapc/), an AI healthcare startup that helps hospitals improve their medical coding and reimbursement workflows. I worked on it from 2019-2025 - yes, we started right after the "Attention is all you need" paper came out. We trained and deployed transformer-based systems on private clinical data for hospitals across North America. We got really good at fine-tuning these systems (on a single 24-48 GB GPU :P), building them into our own workflow software, and deploying them in mission-critical enterprise settings on-premise. I specifically shipped our first MVP (built it in a hospital), and ended up managing a team of 25 ML researchers and engineers.

- Before that, I trained to be a medical doctor at the University of Toronto, and worked as a clinical AI researcher at the [Vector Institute](https://vectorinstitute.ai/) (the academic home of Geoff Hinton). I focused on building and evaluating early-transformer clinical NLP pipelines for clinical text. I don't really have a CS degree, but taught myself how to code in 2013, and no, I don't practice medicine (I left to build my startup).

- I believe AI can be a massive force for improving our collective consciousness and reducing suffering, but it has many risks. I'm now focused on building better AI for mental and spiritual health, but this is still early days.

---

## Why Am I Writing This?

This is the manual for AI programming, at least according to my own experience.

The reality is that things are changing - AI is here, for better or worse. If you are technical or non-technical, the playing field has been massively reset. There are new mental models and first principles for digital productivity with these systems, and we are just starting to really figure them out.

A huge issue is that there is so much evolution in AI tooling - models, paradigms, etc. - and it's all happened so fast. I feel overwhelmed every day and it just keeps piling on.

I have spent lots of time building and tinkering, and I have found out some interesting stuff. Some may be useful, some not, but my goal is to help you do something useful in your life with AI today. If this manual genuinely does that, it's good enough for me. I really do believe that even with current AI capabilities anyone can be 10x more productive.

What I will share is mostly from my personal experience - it may not be accurate, it is definitely not formal or academic research, and it might be outdated by the time you read it. But hopefully it will spark some inspiration into how to start using this powerful tech.

It will help if you are technical, but you don't need to be to understand and apply these principles.

For general ease of reference, I called this general approach "morphic programming." I think it sounds cool tbh, and it references one of the first principles I will share.

---

## How Is This Manual Structured?

I tried to make this as short and simple as possible, as well as clear as possible. People don't have much time these days, so hopefully you can make it through the end in one sitting.

**Part 2: First Principles** - I will share 9 first principles I have started noticing when working with these systems. I have lots more, but want to get the most powerful/fundamental ones out first, and will work on better testing/defining the rest - maybe you guys can help. If you want to skip everything else, just read these. I'm sure I missed some, so please give me some feedback. 7 of these principles can be directly applied now, 2 are more experimental - they might not be immediately useful, but I think they will be more and more useful mental models as the underlying models get smarter.

**Part 3: System Design** - Key system design principles for making morphic programming work, including architecture, tools, and scaffolding.

**Part 4: Practical Tips** - What actually matters and what doesn't, plus the psychological aspects of programming with AI that are usually not covered.

**Part 5: Conclusion** - Parting words and future topics I'm thinking of exploring.

I'm also going to be focused on practical applications, less so formalization of these concepts (although I'm sure many of them can be interesting areas of research).

Finally, there is a lot I will not cover for the sake of brevity - e.g. engineering best practices, MCPs, specific execution/orchestration, advanced context engineering, etc. Some of these I might cover later, but I find that they are well covered elsewhere, and this manual is designed to focus on first principles and mental model shifts you must make to maximally leverage these AI tools.

---

## This Manual Is Free

I don't need anything from you. If you gained value from this manual, please share with your friends or someone you care about. Or post a screenshot or quote on your socials and why you found it useful. I'm happy if this helps at least 1 person use these systems in a better way.

Also leave feedback and your genuine comments/thoughts on the pinned posts in my socials. I have a lot more principles, and a lot more advanced topics to cover, but wanted this manual to be as accessible as possible. If there's interest, I'll make more of these, especially as things continue to evolve, and I will incorporate your insights and feedback where possible.

---

## A Few Disclaimers

**Yes, this manual was AI generated.** However, the core ideas, first principles, and outline for this manual are all my own ideas, and specifically from my direct experience working with CLI agents.

For further clarity, I asked the AI to polish my writing, add working examples/prompts, and add diagrams where reasonable. I did NOT do any initial brainstorming with the AI (e.g. "brainstorm 10 first principles for morphic programming"), and did not ask it to generate net new ideas or insights. I've never written a book before, and this was the fastest way to get this information out into the world in a reasonably accessible format.

**Another disclaimer** - always use your own intuition and common sense. Don't take what I say at face value. Test it, modify it, and if it does not work for your use case, don't use it. AI programming is as much an experimental art as it is rigorous science.

For example, from my experience at Semantic Health, some of the advice or principles might not make sense if you are in mission-critical, enterprise, or highly regulated industries. You might have to be a lot more rigorous and more precise with your natural language code (but know this will come at the cost of speed and leverage).

Finally, I wrote this in about a day so please forgive any imprecision or inaccuracies. I'm just trying to get the key ideas out and will refine them when I have time.

---

# Part 2: First Principles of Morphic Programming

These are some of the most powerful first principles I've come across for creating agentic AI systems to do actually useful work. Most of my experience comes from Claude Code and Gemini-CLI (but much more so Claude). I expect them to become even more powerful as the underlying LLMs get smarter and more capable. The examples I give are going to be software engineering/coding specific, but they can be applied to any digital task.

**Note on examples:** The examples in this manual are simplified to give you inspiration. You will need to expand and tailor the morphic code for your specific use case.

---

## Principle 1: Morphability

The first key shift you must make is to think of natural language as your new programming language. **English is now code.**

I'm always tempted to dive into the weeds and understand every line of code, but the more you can resist that temptation, the faster you will move. You can always dive in if things go wrong. If you don't agree, that's fine - the principles below will still be useful.

So instead of typical code (like Python or JavaScript), your new code is any natural language-based set of instructions that you give to an AI agent to execute. This includes: direct prompts, markdown files (containing prompts, a series of prompts, workflows as a series of executable steps), slash commands (referencing a set of markdown files), etc.

For sake of simplicity, I will just call the set of this natural language code the "morphic code" or "morphic programming" of the system.

**Why morphic?** Because the code is in natural language, it can "morph" on every new execution of that code. This is a subtle but powerful distinction from traditional programming.

**Example 1: Morphing a Test Command**

**Context/Problem:**
You're working with a CLI agent and you've made a custom slash command, `/run-tests`, which references a markdown file containing a set of testing steps an LLM must execute on any new code changes since the last commit. You want to run your standard tests, but also add a specific focus on regression testing for just the API code.

**How the Principle Helps:**
Instead of creating a completely new command or manually describing all the testing steps, you can "morph" the existing command. You invoke it with additional instructions, and the model is smart enough to execute the variant while maintaining the integrity of the original instructions.

**Morphic Code:**
```
# Standard invocation
/run-tests

# Morphed invocation
/run-tests but add a new test to specifically focus on regression,
and focus only on the /api code
```

This seems like a subtle nuance, but we were able to morph the slash command to our current needs - in this case we needed a new test and wanted to focus on a subset of the code. We still get all the benefits of the original command, but now the model executes them in a more tailored manner.

Morphing became especially more reliable with Opus 4.5, which is able to follow more aggressive morphing commands, as well as sophisticated multi-step instructions. It can still fail if your morph is too aggressive, but I think over time this will be a non-issue.

**Example 2: Morphing a Build Command (Coding)**

**Context/Problem:**
You have a `/build-feature` command that takes a user story and implements it following your team's standard process: create a branch, implement the feature, write tests, and create a PR. But for this particular feature, you want to skip the PR creation because you're still experimenting.

**How the Principle Helps:**
You morph the command inline rather than creating a separate `/build-feature-no-pr` command.

**Morphic Code:**
```markdown
# The original /build-feature command contains these steps:
## /build-feature workflow
1. Create feature branch from main
2. Implement the feature according to user story
3. Write unit tests
4. Run all tests
5. Create PR with description

# Morphed invocation:
/build-feature for user story: "Add dark mode toggle to settings page"
but skip step 5 (PR creation) since we're still experimenting
```

**Key insight:** This morphing capability of a single piece of morphic code means that this code can now be leveraged in a potentially limitless number of ways - each slightly different but overlapping with the initial instructions. Every line of code is significantly more useful as it can encode significantly more work and types of work. This means that this code is much more robust to changing tasks/needs, yet generally maintains its stability (the morphing does not permanently alter the original markdown file).

**A note on non-determinism:** This is not the same as the non-deterministic behavior of current LLM systems. We know that current LLMs are non-deterministic - you can run the same prompt multiple times and get different answers each time. That is a limitation. Morphability is an intentional capability - you are explicitly instructing the model to vary its execution.

A byproduct of coding this way is that we can ship morphic code much faster - it does not need to be fully precise or accurate as it can be morphed. But do this at your own risk. Sometimes performance will degrade if the original code is not fully reflective of what you wanted.

**Key Takeaway:** View your AI system as a set of morphable natural language code. Pay particular attention to the starting set of code, and design it in such a way for maximum morphability. Each piece of morphic code can be invoked in countless variations without modification.

---

## Principle 2: Abstraction

Let's say you complete a task with your agent by prompting it a number of times - you had a conversation with it and you told it what needed to be done and worked with it until it was done. Let's call this a task, or unit of "work."

For example, you're coding a React app, and you have a user story. You want the agent to create an implementation plan, execute it, test it, then commit the feature from that user story. The simplest way to do this is by having a sequential conversation with the agent - walking through every step of the process, reviewing its work after every step, and then moving onto the next step when you're happy.

Let's say it successfully builds you the feature, tests it, and commits it. Now you have 10 more features, and you aren't really looking forward to repeating that process over and over again.

What if you could say to the agent: "Now I'm going to give you 10 more user stories and I want you to repeat the same process we just followed for each and in the same standard/quality." This is a 10x more powerful task you just gave the agent, but you have no guarantee it will follow the same process in the same way for each of the tasks. And what if your agent crashes or you exit the agent?

**The solution is abstraction.** You can abstract any task into morphic code - a slash command, a workflow, or a markdown file.

Abstraction means that the code should not be specific to the given feature (or task), but should generally outline the manual process you followed with the AI to do the task or unit of work.

**Example 1: Abstracting a Feature Development Process**

**Context/Problem:**
You just completed a 2-hour session with your agent to build a new feature. It took 15 manual steps and several back-and-forths. Now you have 10 more features to build and don't want to repeat this manual process.

**How the Principle Helps:**
You ask the agent to abstract the conversation into a reusable command. This captures the essence of your manual process in morphic code.

**Morphic Code:**
```markdown
# /build-feature command

## Inputs
- User story (required)
- Priority level (optional, default: medium)
- Test coverage target (optional, default: 80%)

## Workflow Steps

### Step 1: Planning
- Read the user story carefully
- Identify affected files and components
- Create implementation plan with estimated changes
- Present plan for user approval before proceeding

### Step 2: Implementation
- Create feature branch: `feature/[story-slug]`
- Implement changes following existing code patterns
- Add inline comments for complex logic only

### Step 3: Testing
- Write unit tests for new functionality
- Ensure test coverage meets target
- Run full test suite, fix any regressions

### Step 4: Documentation
- Update relevant documentation if API changes
- Add JSDoc comments for new public functions

### Step 5: Commit and PR
- Create atomic commits with clear messages
- Open PR with description linking to user story
```

Now the unit of work that took you 15 manual steps and 2 hours is represented in morphic code. Next time you might be able to one-shot it, and if you can't, your time to complete will have significantly gone down. AND you now have morphic code that can be used for a huge number of similar tasks.

**Example 2: Abstracting with Configuration**

**Context/Problem:**
Your feature development process works great, but different types of features need different settings - some need extensive testing, others are quick fixes that don't need PR reviews.

**How the Principle Helps:**
You abstract the variable parts into a configuration file, keeping the workflow stable while allowing customization.

**Morphic Code:**
```yaml
# feature_config.yaml
feature_types:
  standard:
    test_coverage: 80%
    require_pr_review: true
    require_documentation: true

  hotfix:
    test_coverage: 90%
    require_pr_review: true
    require_documentation: false
    branch_prefix: "hotfix/"

  experiment:
    test_coverage: 50%
    require_pr_review: false
    require_documentation: false
    branch_prefix: "experiment/"
```

```markdown
# Updated /build-feature command
Read the feature_config.yaml and apply settings based on the
feature_type parameter. Default to "standard" if not specified.

/build-feature type=hotfix story="Fix login timeout issue"
```

**A generic abstraction prompt:**
```
Review our conversation and abstract the core workflow we followed
into a reusable command. Remove any business-specific details and
focus on the general process. Output as a markdown file I can save
as a slash command.
```

You can also apply this principle in a generic `/cleanup` command that reviews the existing conversation and looks for abstraction opportunities - more recursive leverage.

**Key Takeaway:** Any unit of work can theoretically be abstracted into reusable morphic code. When you complete a multi-step task manually, ask yourself: "Can I abstract this into a command so I never have to do it manually again?"

---

## Principle 3: Recursion

As you abstract specific tasks and units of work, you can now go up a level in the "work" hierarchy. In the same way we abstracted over the need to directly program with Python or JavaScript with morphic programming, you can think of every digital workflow or task as abstractable.

Think about how we went from manipulating bits in computers to now just natural language, or how we went from DNA to organs to an organism in biology. This is already a fundamental rule of life, but we are applying it in the context of morphic programming.

**Recursion is a powerful mental model for morphic programming** - you should aim to recursively move up to more and more leveraged units of work. Do this obviously in line with how good the underlying system or intelligence is (see End-to-End Autonomy for how to think about this).

**Example 1: Stacking Commands**

**Context/Problem:**
You have three separate commands that you always run together: `/build-feature`, `/run-tests`, and `/deploy-staging`. Every time you finish a feature, you manually invoke all three.

**How the Principle Helps:**
You create a higher-level command that stacks the lower-level ones, giving you more leverage from a single invocation.

**Morphic Code:**
```markdown
# /ship-feature command (recursive stack)

## Description
Complete feature development workflow from user story to staging deployment.
Stacks: /build-feature -> /run-tests -> /deploy-staging

## Workflow
1. Execute /build-feature with the provided user story
2. If build succeeds, execute /run-tests
3. If tests pass, execute /deploy-staging
4. Report final status with links to PR and staging environment

## Usage
/ship-feature story="Add user preferences panel"
```

Now one command does what three used to do. But you can go further:

```markdown
# /ship-sprint command (even more recursive)

## Description
Process an entire sprint's worth of user stories.
Stacks: /ship-feature (multiple times) -> /create-release-notes

## Workflow
1. Read sprint stories from stories.md
2. For each story, execute /ship-feature
3. Collect all PR links and changes
4. Execute /create-release-notes with collected changes
5. Present summary for review
```

**Example 2: Recursive Self-Improvement**

**Context/Problem:**
You want your system to not just execute commands, but to improve its own commands based on the first principles you've taught it.

**How the Principle Helps:**
You encode the principles themselves into the agent's context, so when it maintains or improves itself, it applies those principles.

**Morphic Code:**
```markdown
# /evolve command (meta-recursive)

## Description
Review recent work and improve the morphic programming itself.
This command applies the first principles to evolve its own codebase.

## Workflow
1. Review the last 5 completed tasks
2. For each task, ask: "Could this have been abstracted better?"
3. For each existing command, ask: "Has this become too complex?"
4. Propose improvements following these principles:
   - Maintain internal consistency
   - Reduce morphic complexity where possible
   - Increase abstraction where patterns repeat
5. Present proposed changes for approval before applying
```

**Key insight:** You can recursively nest commands in each other, but be careful. In my experience, recursion tends to break if the stack level is more than 2 or 3 deep with current models. I expect this to improve as models become more intelligent, and at some point they may be able to do recursive self-improvement on their own (see the self-improvement example above).

**Key Takeaway:** Each level of abstraction enables the next. Stack commands on commands to multiply your leverage. The goal is to recursively move up to higher and higher units of work until a single invocation accomplishes what used to take hours or days.

---

## Principle 4: Internal Consistency

For your morphic code to function reliably and optimally, it must maintain its internal consistency.

**Internal consistency** is basically how consistent each instruction is with every other instruction:
- Does an instruction include a reference or description of another instruction that is deprecated? (This is the most harmful one)
- Does the documentation/context not reflect changes to an instruction or new instructions?
- Do instructions contradict each other?
- Do multiple instructions describe overlapping tasks?

So you need a command or process to maintain internal consistency as you evolve the morphic code and complete units of work. Ideally, units of work should also provide the system with learning opportunities to evolve its morphic code (see the section on System Design below for how to think about this).

**Example 1: The Cleanup Command**

**Context/Problem:**
You've been rapidly iterating on your system. You've added new commands, modified existing ones, and your documentation is now out of sync. Some commands reference workflows that no longer exist. Your README mentions 5 commands but you now have 12.

**How the Principle Helps:**
A dedicated cleanup command performs comprehensive consistency checks after every major unit of work.

**Morphic Code:**
```markdown
# /cleanup command

## Description
Post-task consistency verification and maintenance.
Run after completing any significant work.

## Consistency Checks

### 1. Documentation Sync
- Compare README command list with actual commands
- Flag any mismatches for update

### 2. Reference Validation
- Scan all commands for references to other commands
- Verify referenced commands exist
- Flag deprecated or renamed references

### 3. Progress Tracking
- Ensure progress log is updated with recent work
- Check that completed tasks are marked done

### 4. Configuration Drift
- Compare config files with their documentation
- Flag any undocumented parameters

### 5. Duplicate Detection
- Identify commands with overlapping functionality
- Suggest consolidation opportunities

### 6. Context Review
- Review the key context files used on priming
- Ensure they are up to date with recent changes
- Flag any stale or outdated context

## Output
Report findings and propose fixes. Apply fixes only with approval.
```

**Example 2: Preventing Consistency Drift in Code**

**Context/Problem:**
You're building an API and you've renamed an endpoint from `/users` to `/accounts`. But your frontend code, tests, and documentation all still reference `/users`.

**How the Principle Helps:**
You add consistency checking to your development workflow.

**Morphic Code:**
```markdown
# Add to /build-feature workflow

## Step 2.5: Consistency Check (after implementation, before testing)
Before running tests, perform a consistency check:

1. If any public API was changed (renamed, deprecated, modified):
   - Search entire codebase for references to old API
   - Update all references to match new API
   - Update API documentation
   - Update any test fixtures or mocks

2. If any shared types were modified:
   - Find all files importing those types
   - Verify they still compile correctly

3. If any configuration schema changed:
   - Verify all config files match new schema
   - Update config documentation

Flag any issues found and fix before proceeding to tests.
```

You can easily see that if the morphic complexity goes up (see the Morphic Complexity principle below), it becomes harder to maintain internal consistency. The two are inversely related.

**Key Takeaway:** Internal consistency is the immune system of your morphic codebase. Build automated consistency checks into your workflow, and run them frequently. Drift is the silent killer of morphic systems.

---

## Principle 5: Reproducibility

A key goal of any morphic system is that it should be reproducible almost instantly. This means that it should be able to be turned off, and then turned on again and you can pick up where it left off without meaningful performance degradation on the task.

**You know your system is reproducible when you don't get pissed off when your IDE or Claude Code instance crashes.** You can re-prime it (e.g. with a `/prime-agent` command), and in a few minutes pick up where you left off.

However, it's really hard to have fully lossless reproducibility, so just aim for good enough. Your system should at least know what the key tasks/plans are, and the main system and activity-specific context at minimum. I think systems are more unstable if the reproducibility is more lossy.

If we have decently lossless reproducibility, we can:
- Be robust to crashes
- Clone agents and work in parallel (this is limited by compute now)
- Have a clear audit and save state for the system (maximum transparency)

**Example 1: The Prime Command**

**Context/Problem:**
Your agent just crashed mid-task. You start a new session and the agent has no idea what you were working on, what the project context is, or what tasks are pending.

**How the Principle Helps:**
A prime command rapidly loads all essential context so you can resume work immediately.

**Morphic Code:**
```markdown
# /prime-agent command

## Description
Rapidly restore agent context after a fresh start or crash.
Goal: Full working context in under 2 minutes.

## Context Loading Sequence

### 1. Core Documentation (30 seconds)
Read these files to understand the system:
- README.md (project overview)
- CLAUDE.md or AGENT.md (agent instructions)

### 2. System-Wide Context (MUST READ)
Read key context files that are always relevant:
- User preferences and style guide
- Project-specific business context
- Key constraints and requirements

### 3. Current State (30 seconds)
Read these files to understand where we are:
- progress_log.md (last 20 entries)
- current_tasks.md (active work)

### 4. Active Context (30 seconds)
If a specific task is in progress:
- Read the relevant plan file
- Read files mentioned in the plan

### 5. Quick Verification (30 seconds)
- Run `git status` to see uncommitted work
- Run `git log -5` to see recent commits
- Summarize current state to user

## Output
"I'm now primed. Here's where we left off: [summary].
Ready to continue with [current task]."
```

**Example 2: The Rebuild Command**

**Context/Problem:**
You want to set up the same system on a new machine, or help a teammate get the same development environment. Or you want to test if your system can be fully reconstructed from its specification.

**How the Principle Helps:**
A rebuild command can reconstruct the entire system from a single specification document.

**Morphic Code:**
```markdown
# /rebuild command

## Description
Reconstruct the complete system from specification.
Proves the system is fully documented and reproducible.

## Inputs
- build_spec.md: Complete specification of the system

## Workflow
1. Read the build specification document
2. Create directory structure as specified
3. Create all documentation files
4. Create all command files
5. Create all configuration files
6. Initialize git repository
7. Run /prime-agent to verify setup
8. Report success/failure with any issues

## The Build Specification Should Contain:
- Directory structure
- All file contents or templates
- Configuration defaults
- Command definitions
- Documentation outlines
```

**Key elements for reproducibility:**
- **Single source of truth**: All state lives in files that can be read
- **Progress logs**: Detailed logs of what was done and when
- **Plans as files**: Active work plans saved to disk, not just in conversation
- **Git everything**: All morphic code versioned in git

**Key Takeaway:** Design your system so that a fresh agent can reach full working context in minutes, not hours. If you dread crashes, your system isn't reproducible enough. The goal is crash-resilience through comprehensive context documentation.

---

## Principle 6: Morphic Complexity

One limitation of morphic programming is that you will reach a point when the morphic code is too complex. The set of all natural language instructions is associated with a level of complexity, and at some level, the system will start to break down. Some symptoms:
- The system performance will degrade
- It will start to forget how to execute some of your basic commands
- It will take way too long to maintain internal consistency
- Not following all instructions for a command (e.g. if there are too many nested commands or specific steps where it has to reference other assets)
- Doing an instruction but not in the originally intended way

**You can think of morphic complexity generally as:**
1. The number of unique instructions contained in your code
2. The interconnectedness of the instructions (most basic connection is a reference to another instruction)
3. The difficulty of each instruction (if an instruction contains a super highly complex task, that instruction is more complex)

I'm sure someone can mathematically model this out, but just go off intuition and symptoms you start seeing in the system.

**Example 1: Recognizing Complexity Symptoms**

**Context/Problem:**
Your `/deploy` command used to work flawlessly. Now it sometimes skips the testing step, occasionally forgets to update the changelog, and once deployed to production instead of staging.

**How the Principle Helps:**
You recognize these as symptoms of morphic complexity and take action to simplify.

**Signs Your System Is Too Complex:**
```
SYMPTOM CHECKLIST

[ ] Commands skip steps they used to complete reliably
[ ] Agent asks for clarification on commands that were previously clear
[ ] Nested commands fail more than direct commands
[ ] Consistency checks take longer than the actual work
[ ] Agent seems "confused" about which command to use
[ ] Similar commands have diverged in behavior
[ ] Documentation updates take as long as feature development
```

**Example 2: Refactoring for Simplicity**

**Context/Problem:**
You have 25 commands, many of which overlap or are rarely used. Your `/cleanup` command references 15 other files and takes 5 minutes to execute.

**How the Principle Helps:**
You manually refactor to reduce complexity while preserving output quality.

**Morphic Code:**
```markdown
# Refactoring approach

## Step 1: Audit
List all commands with:
- Last used date
- Frequency of use
- Number of steps
- Number of references to other commands/files

## Step 2: Consolidate
- Merge commands with >70% overlap
- Delete commands unused in 30+ days
- Flatten unnecessarily nested commands

## Step 3: Simplify
For each remaining command:
- Can any steps be removed without degrading output?
- Can references be inlined if they're only used once?
- Can configuration be simplified?

## Step 4: Verify
- Run all commands to ensure they still work
- Measure execution time (should decrease)
- Run /cleanup and verify it completes faster
```

When you see degradation happening, congrats - you've probably over-engineered the system. You need to refactor your morphic code back down to a reasonable level of complexity.

I usually like to manually refactor as this is a very sensitive change to the morphic code. Start with areas you know are too complex, and chat with the agent - focus on making minimal changes but simplifying the code to preserve output quality. Reducing token count is a good proxy, but also refactor connection points like references to other morphic code.

**Key Takeaway:** There's a ceiling to how complex your morphic system can get before it starts degrading. Monitor for symptoms of over-complexity, and proactively refactor to stay below the threshold. Simpler systems are more reliable systems.

---

## Principle 7: End-to-End Autonomy

When evaluating the usefulness of your systems, you should always evaluate relative to real-life, business-specific tasks (or units of work) that you are trying to solve. I don't really concern myself with benchmarks so much as I'm mostly a builder and focused on applied AI, so that is my bias. But I also don't think benchmarks are entirely representative of the practical usefulness of AI systems.

**If your system can one-shot a given task, then it is end-to-end (E2E) autonomous for that task.** For clarity, if you have to intervene and give at least 1 guidance/feedback to the system after the planning stage, then the task is not E2E autonomous.

For any given AI system, there will be a set of tasks that it can complete E2E autonomously. At some point, you will reach a task complexity or category of tasks that it cannot E2E autonomously complete. I informally define this as the **E2E complexity** of the system.

**Example 1: Measuring E2E Complexity**

**Context/Problem:**
You want to understand what your system can actually do autonomously versus what requires your intervention.

**How the Principle Helps:**
You create a practical test suite based on real tasks, not synthetic benchmarks.

**Morphic Code:**
```markdown
# E2E Autonomy Test Suite

## Level 1: Simple (should be 100% E2E)
- [ ] Add a console.log statement to debug a function
- [ ] Rename a variable across a file
- [ ] Add a comment to explain complex code
- [ ] Create a new empty component file

## Level 2: Moderate (target: 80% E2E)
- [ ] Implement a single CRUD endpoint
- [ ] Add form validation to existing form
- [ ] Write unit tests for existing function
- [ ] Fix a clearly defined bug

## Level 3: Complex (target: 50% E2E)
- [ ] Implement a feature from user story
- [ ] Refactor a module to new pattern
- [ ] Add authentication to existing routes
- [ ] Optimize a slow database query

## Level 4: Advanced (target: 20% E2E)
- [ ] Build complete feature across frontend/backend
- [ ] Migrate database schema with data
- [ ] Implement third-party API integration
- [ ] Debug a production issue from logs

## Level 5: Expert (target: 5% E2E)
- [ ] Architect a new microservice
- [ ] Complete system refactoring
- [ ] Performance optimization across stack
```

This is important to practically know and use. For example, a system that can one-shot a fully functional iOS app according to your product/business specs (System 1) is way more useful than one that can one-shot a single feature of that app (System 2). System 1 has much higher E2E complexity than System 2.

**Example 2: Using E2E Complexity to Decide Task Delegation**

**Context/Problem:**
You have a task and need to decide: should you just give it to the agent and walk away, or should you stay engaged and provide guidance?

**How the Principle Helps:**
You match task complexity to your system's proven E2E capability.

**Decision Framework:**
```
TASK DELEGATION DECISION

1. Estimate task complexity (1-5)
2. Check your system's E2E success rate at that level
3. Decide:

If success_rate > 80%:
  -> Delegate fully, check result at end

If success_rate 50-80%:
  -> Delegate with checkpoints (review after each major step)

If success_rate < 50%:
  -> Break down into smaller tasks OR
  -> Stay engaged and guide throughout
```

You can also experiment with giving it more complex tasks than it can handle and see if it can one-shot it. This is probably most useful to do with the release of new LLM models as they might have step-function increases in performance for your tasks.

**A note on multimodal models:** Multimodal models are way more powerful (like Gemini) because you essentially increase the task complexity they can handle (they can now handle tasks involving multiple input and output data modalities). These models are still early, but they will unlock a lot of cool use cases.

**Key Takeaway:** Know your system's E2E complexity ceiling for different task types. Delegate appropriately - some tasks can be fully automated, others need human-in-the-loop. As models improve, continuously test if that ceiling has risen.

---

## Principle 8: Token Efficiency (Experimental)

Another way to look at work leverage is at the token level. Each token encodes some instruction (or partial instruction) to the system about what work you want it to do.

Naturally, some tokens can encode more work than others:
- A slash command `/deploy` encodes significantly more work than the word "exit"
- Some tokens encode no work (e.g. the word "the")

I define **token efficiency** as the amount of work a token encodes. I'm sure there's some way to formalize this using information theory, but again we're focused on practical guidance.

Since we don't yet have infinite context windows, it is decently important to think about this. But you might be over-engineering if you think about this for every word. I think this is just a generally interesting mental model for you to teach the agent, as it can optimize its own morphic programming to increase token efficiency.

**Example: Understanding Token Efficiency**

**Context/Problem:**
You're hitting context limits when running complex commands. You want to understand which parts of your morphic code are most "efficient" in terms of work output per token.

**How the Principle Helps:**
You analyze your commands to understand token efficiency and optimize the highest-leverage parts.

**Analysis Framework:**
```
TOKEN EFFICIENCY ANALYSIS

Command: /cleanup
Tokens: ~15 (including the slash)
Work encoded: 15 distinct verification steps
Token efficiency: ~1 step per token (HIGH)

Command: "Please check if all documentation is up to date"
Tokens: ~10
Work encoded: 1 verification step
Token efficiency: 0.1 steps per token (LOW)

Insight: The /cleanup command is 10x more token-efficient
because it references a detailed workflow file.
```

The more work you can pack per token, the more efficient the context usage, but also the more work leverage you can get. This means that it's very important what words you use when programming the system.

This might not be super relevant for systems now, as task complexity is still not that high, but as the underlying models get better and context windows fill up with more sophisticated instructions, this might become more important.

**Key Takeaway:** Token efficiency is about maximizing work output per token of input. Slash commands that reference detailed workflows are more token-efficient than inline instructions. As you build more sophisticated systems, this becomes a useful optimization lens.

---

## Principle 9: Mutation and Exploration (Experimental)

If you have sufficiently abstracted a good amount of the morphic programming and have a few abstracted config files, you can run experiments to determine if there is more optimal programming to complete your task. This can be done by you or the system, but in the beginning it's best if you guide it (I have not yet gotten to autonomous experimentation).

**The key principle is this:** Once you abstract a workflow, you will have some part of it that is configurable (e.g. represented in JSON or YAML config files). This contains the key parameters that might be important for orchestrating that workflow.

You can then mutate various parameters by defining a mutation rate (e.g. very aggressive, conservative). This allows you to generate new configs with variances in parameters according to your mutation rate. I'm sure there is some rigorous math or formalization here (with some stats), but let's keep it simple.

**Example 1: Controlled Parameter Mutation**

**Context/Problem:**
You have a code review workflow that works okay, but you wonder if different parameters would produce better results. How thorough should the review be? Should it focus on security, performance, or code style?

**How the Principle Helps:**
You define an exploration rate that controls how much variation to introduce when generating new configs.

**Morphic Code:**
```yaml
# code_review_config.yaml
metadata:
  exploration_rate: MEDIUM  # LOW | MEDIUM | HIGH

parameters:
  thoroughness: 7  # 1-10 scale
  focus_areas:
    - security: 0.4
    - performance: 0.3
    - style: 0.3
  max_comments: 10
  require_approval: true

# Exploration rate meanings:
# LOW: Vary parameters by +/- 10%
# MEDIUM: Vary parameters by +/- 30%, can swap focus priorities
# HIGH: Vary parameters by +/- 50%, can add/remove focus areas
```

```markdown
# /experiment command

## Usage
/experiment generate-variants code_review_config.yaml count=3

## Output
Generates 3 variant configs based on exploration_rate:

Variant 1: thoroughness=9, security=0.5, performance=0.3, style=0.2
Variant 2: thoroughness=5, security=0.3, performance=0.4, style=0.3
Variant 3: thoroughness=7, security=0.4, performance=0.2, style=0.4

Run each variant on test cases and compare results.
```

**Example 2: Self-Improvement Loop**

**Context/Problem:**
You want your system to not just run experiments, but to learn from them and improve its own morphic programming.

**How the Principle Helps:**
You create a feedback loop where experiment results feed back into the system's configuration.

**Morphic Code:**
```markdown
# Self-improvement cycle

## Step 1: Baseline
Run current config on 10 representative tasks
Record: success rate, time, quality score

## Step 2: Mutation
Generate 3 variants using exploration_rate=MEDIUM
Run each variant on same 10 tasks
Record results

## Step 3: Selection
Compare variant results to baseline
If any variant beats baseline on all metrics:
  -> Propose adopting variant as new baseline

## Step 4: Evolution
If adopted, the new baseline becomes the starting point
Repeat cycle

## Guard rails
- Never auto-apply changes (require human approval)
- Keep history of all experiments
- Can always roll back to any previous config
```

I almost didn't include this principle because it's still very experimental, but I think this can be used powerfully once your system is stabilized. You need a clear evaluation metric - or reward signal - but to make things simple, pick something business-specific related to your actual problem.

As you can see, this approach can probably be formalized into an RL paradigm where the agent can self-improve according to some signal - but you define self-improvement as it making changes to its own morphic programming. I'm not an RL expert, but I will explore this at some point.

**Key Takeaway:** Once your system is stable, you can introduce controlled mutation to explore better configurations. Define clear success metrics, generate variants, test them, and adopt improvements. This is the path toward systems that improve their own morphic programming.

---

# Part 3: System Design for Morphic Programming

What are some of the key system design principles, including architecture, tools, and scaffolding, needed to make this work? I will keep this very simple. Only the most fundamental primitives for getting this system up and running. Future parts will go into more advanced topics.

For a reference list of generic commands you can use in any morphic system, see the [Appendix: Generic Commands Reference](#appendix-generic-commands-reference).

---

## Repository Structure

Your morphic system should live in a git repository with a clear structure. Here's a minimal but effective organization:

```
my-morphic-system/
├── README.md              # Project overview
├── AGENT.md               # Agent instructions (like CLAUDE.md)
├── commands/              # Slash command definitions
│   ├── prime.md
│   ├── cleanup.md
│   ├── build-feature.md
│   └── ...
├── workflows/             # Multi-step process definitions
│   ├── development.md
│   ├── testing.md
│   └── ...
├── configs/               # Configuration files
│   ├── default.yaml
│   └── ...
├── context/               # Contextual information
│   ├── project/           # Project-specific context
│   └── system/            # System-wide context
├── progress/              # State and progress tracking
│   ├── progress_log.md
│   ├── current_tasks.md
│   └── plans/
└── src/                   # Your actual code (if applicable)
```

**Figure 1: Repository Structure**

```
┌─────────────────────────────────────────────────────────────┐
│                    MORPHIC SYSTEM REPO                       │
├─────────────────────────────────────────────────────────────┤
│  README.md + AGENT.md                                        │
│  (Core documentation - what and how)                         │
├──────────────────┬──────────────────┬───────────────────────┤
│    commands/     │    workflows/    │      configs/         │
│  ┌──────────┐    │  ┌──────────┐    │   ┌──────────┐        │
│  │ prime.md │    │  │ dev.md   │    │   │ app.yaml │        │
│  │cleanup.md│    │  │ test.md  │    │   │agent.yaml│        │
│  │build.md  │    │  │deploy.md │    │   └──────────┘        │
│  └──────────┘    │  └──────────┘    │                       │
├──────────────────┴──────────────────┴───────────────────────┤
│  context/                    │  progress/                    │
│  ┌─────────────────────┐     │  ┌─────────────────────┐      │
│  │ project/ (business) │     │  │ progress_log.md     │      │
│  │ system/ (technical) │     │  │ current_tasks.md    │      │
│  └─────────────────────┘     │  │ plans/              │      │
│                              │  └─────────────────────┘      │
└──────────────────────────────┴───────────────────────────────┘
```

---

## Use CLI Agents

If you are still using conversational UIs you will not be able to really leverage the power of these principles. The reason is that CLI agents can theoretically do any arbitrary task on your computer (given sufficient permissions or tools). This means they have much higher E2E complexity than traditional conversational interfaces.

Also with CLI agents, you can version and maintain their morphic code in a git repo, which is critical. Every unit of work can be versioned if you want it to, and you can recurse over any unit of work (theoretically).

**Key advantages of CLI agents:**
- Can execute arbitrary commands on your system
- Can read/write files directly
- Can interact with git
- Can run tests, builds, deployments
- Can be automated and scripted

You can also design the system so that it does not matter which CLI agent you use - this is very important to me because I eventually want to try using open source models.

**Important disclaimer:** In my experience, Claude Code (specifically Opus 4.5) is significantly further ahead in terms of being able to understand and follow these principles compared to Gemini 3.0 Flash. Claude Code can handle complex multi-step workflows, maintain internal consistency across long sessions, and follow nuanced morphic instructions much more reliably. I have not extensively tested other agents, so your mileage may vary. This gap may close as models continue to improve.

Over time, CLI agents are theoretically going to be E2E autonomous for arbitrarily more complex tasks. The CLI is the most primitive and powerful interface to a computer, so stay at this level.

Your morphic programming should ideally be contained in markdown files. You can experiment with other formats, but I think markdown is most versatile and rich and models can handle it well.

---

## Use Git

With morphic programming, git now stores the morphic code in addition to your source code. This also requires a mental model shift.

You can theoretically orchestrate any digitally based task through morphic programming and Git, and store the morphic code as well as artifacts, logs, and learning in Git. Git becomes a living, breathing snapshot of your morphic system, and allows you to orchestrate multiple activities through multiple morphic agents from a single source of versioned truth. This is the most powerful way to build these systems.

**What to version control:**
- All morphic code (commands, workflows, configs)
- All documentation
- Progress logs and plans
- System context files
- Agent instruction files

**Git best practices still apply:**
- Modular, detailed commits
- Clear commit messages
- Document changes
- Run tests before committing

Morphic code precision does not matter as much as traditional code, but still commit, document, and maintain a clean history. These best practices should all be followed and ideally provided to your code-building agent as context.

---

## Context Engineering

Context is critical. If you don't have the proper context for your system it will not be as useful. Most of your time as a human orchestrator should be in context engineering - what context do I need, how do I format it and provide it in the right way, to maximally prime my agent to complete the task I want to give it.

If you don't give your agent proper context you are setting it up to fail. This is where most of your work will come in when defining new tasks after your system is stable/mature.

**To reiterate: context is just as critical, if not more so, than the prompting, system design, or assets.** You need both context and powerful design for best results. I'm pretty sure you can increase the E2E complexity of any system significantly with just better context engineering.

You should define context at various levels of the system, and clearly scope them in. I like to think in terms of 2 levels:

**Type 1: System-Wide Context**
- User-specific context (your preferences, style, goals)
- Agent-specific context (its role, capabilities, limitations)
- Project-specific context (business domain, technical stack)
- Will be read on every prime/instantiation
- Should be maintained by commands or workflows for maximum internal consistency

**Type 2: Activity-Specific Context**
- Related to completing a specific activity or task
- E.g. for building an app: SDLC docs, product spec, API docs
- Should include: the problem you're solving, your proposed solution, constraints, requirements
- Add supporting documentation where possible

**Figure 2: Context Layering**

```
┌─────────────────────────────────────────┐
│         ACTIVITY-SPECIFIC CONTEXT        │
│  (loaded for specific tasks)             │
│  - Feature specs                         │
│  - Related code files                    │
│  - Task-specific docs                    │
├─────────────────────────────────────────┤
│         SYSTEM-WIDE CONTEXT              │
│  (always loaded on prime)                │
│  - Project overview                      │
│  - Agent instructions                    │
│  - User preferences                      │
│  - Current state (tasks, progress)       │
├─────────────────────────────────────────┤
│         MODEL KNOWLEDGE                  │
│  (built into the LLM)                    │
│  - General programming knowledge         │
│  - Language/framework docs               │
│  - Best practices                        │
└─────────────────────────────────────────┘
```

Spend significant time defining activity-specific context - as much detail or specificity as possible. The most important aspects:
- The problem you are trying to solve
- The vision/solution you think will work
- Constraints or limitations
- Fundamental requirements

If you don't have enough time, just one-shot the context off the dome - sometimes it may work.

---

## A Note on Agent Orchestration

I define a central orchestration agent that I invoke with a priming `/prime-agent` command. This is fully primed to the current state of the system and can spawn new agents if needed.

You can create agents with specific skills and context for each main activity, but this is over-engineering in the beginning.

For now, you can spawn multiple orchestration agents, and prime each with a `/prime-agent`. Have them work on separate tasks and run `/cleanup` on each to maintain internal consistency. I'm sure there are ways to scale this up but I have not needed to right now as I'm limited by AI compute.

Agent orchestration can get a lot more complex - with multi-agent orchestration, implementing as Claude agents, Claude skills, MCPs - I might cover this in a second part, but this is over-engineering for now.

---

## A Note on IDEs and Models

As much as possible, treat specific IDEs (Cursor, Windsurf) and model providers (OpenAI, Anthropic, Google) as arbitrary and interchangeable.

For models, of course they each have strengths and weaknesses, but over time, they will converge to strong enough multi-modal intelligence.

For IDEs, pick the IDE you are most comfortable with.

**For models:** Pick the model that is the current SOTA for your task (e.g. Opus for coding, Gemini/Sora for video gen, etc). These might change over time, so you don't want to design a system that is overly reliant on any one provider.

**The key insight:** LLMs are the lower level unit of compute in this paradigm. Over time they will all be very strong. Right now you can spin up multiple agents in parallel with arbitrary models and have them do different things.

---

## A Note on Vibe Coding

You might be wondering - isn't this just a fancy way of doing vibe coding?

It is and it also isn't.

I do fundamentally believe in the power of vibe coding - the core of it is we are abstracting over the formal programming step, which will allow us to leverage our time significantly more.

However, vibe coding has gotten a bad rap for lacking rigor, principle, reproducibility, and quality.

**My goal with this manual is to share a more principled and rigorous approach to abstracting yourself up and away from formal programming, while still maintaining confidence in the system.**

The first principles I've shared are designed to give you that confidence:
- **Reproducibility** ensures you can always recover state
- **Internal consistency** ensures your system doesn't drift
- **Morphic complexity** warns you when you've over-engineered
- **E2E autonomy** helps you know what to trust

Vibe coding without these principles is risky. Vibe coding WITH these principles is powerful.

---

# Part 4: Practical Tips and Psychology

To be extremely effective with morphic programming, you have to also pay attention to the psychological aspect. If you don't, you might get stuck, build incorrect core beliefs, and ultimately be ineffective in this era. These are usually not covered, but they're important.

---

## What Actually Matters

**Clear vision and conviction** - This is the MOST important skill for 10x productivity. You have to know what you want with high belief. Execution is a commodity now when you can build anything. But you should not build anything. You need to learn the skill of knowing what to build.

As a startup CEO this was my main job. This is not something the AI can do for you now. This was a really good [tweet on this topic](https://x.com/brookejlacey/status/2004615362994901248).

**Thinking like a product manager** - Define clear requirements, success criteria, and constraints before delegating to the agent.

**Taste** - Knowing what good looks like, what to accept and what to reject.

**Authenticity** - Building things that genuinely matter to you, not just what's technically possible.

**You can literally build anything that your mind imagines, but not everything it imagines is worth building.** Human creativity and imagination, authenticity, and taste are going to be the key differentiators in the era of AI and agents. Part of the overwhelm I experience is from lack of clarity about where I'm going or lack of conviction in the end goal. Stay focused, with high conviction, and know what your key values are.

**Don't over-index on LLMs.** They are the low-level unit of compute in more sophisticated AI systems. Let frontier companies improve their intelligence, but focus on abstracting over this unit of compute.

---

## What Does Not Matter

**Being in the weeds** - i.e. doing everything yourself. Resist the temptation.

**Micromanaging the AI** - Unless it is not getting it right, then E2E complexity is too high for current state, and you need to break down the problem.

**Perfection** - The prompts and assets are all morphic, so they do not need to be 100% perfect, just good enough. This will unlock massive leverage and speed. Of course exercise your own judgment, especially if the prompt is in charge of something super business critical.

**The model provider** - Open or closed source, the actual company. There are leaders now and certain models good for certain tasks, but design your system in an abstract/independent way as possible. I'm a big believer in not relying too much on one company. The models themselves (LLMs) should be arbitrary units of compute, nothing more. A well designed morphic system will scale as the underlying models get more and more intelligent.

---

## Psychological Tips

Many of these are experiential and not formal or scientific. You must learn from experimentation and experience.

**Treat agents like your software engineers.** Perhaps the most important psychological mental model to adopt is to genuinely treat these agents like your software engineers. If you have ever managed a team, you will know what I'm talking about.

Current agents are still in their early days, but they are quite capable. A good rule of thumb for now is to treat them like junior/intermediate software engineers. As these models get better and are able to handle more E2E complex tasks, you can treat them like senior SWEs and maybe even tech leads, but not right now.

Part of being a good product manager is learning:

- **Clear expectations** - They should have very clear direction about the problem, expected solution, and any key business context/constraints/requirements. This is not any different from giving an engineer a detailed user story. Both a human and the model need proper context to succeed.

- **Autonomy** - They should have the ability to solve the task in the way THEY think makes sense. Do not micromanage this.

- **Accountability** - If they do not solve the task, or do it incorrectly, you need to give them clear and direct feedback. Do not be emotional. If they are struggling, provide more detailed guidance, do more detailed pulse checks on their work, and maybe even mentor. Resist the temptation to do the work for your employee (whether model or human, this can become micromanaging and de-leverage your own time).

**Don't get attached to your morphic code.** You might be attached to it in the same way you are to formal code. Don't be. It is much more imprecise and in some cases transient. Be okay with completely destroying morphic code and starting from scratch - the cost of doing this is near zero.

**Don't get bothered with precision.** As long as you maintain internal consistency and the outcomes are what you want (features are working, it's building things properly), measure it based on its output, not the process.

**Give your agents tests.** See if they pass or fail. You can tell it you are going to test its capabilities. Always take detailed notes and observations (what it did well on, what it's struggling with), and tell it if it passed or failed. Then run that through your learning command. Here are some example tests I've used:

- **Test example 1:** "Design the next test for yourself, execute it, then abstract/recurse on this process of testing yourself with a command that will create new tests. The goal should be for you to improve yourself based on all the things we talked about."

- **Test example 2:** "Run the /evolve command on your first test. Look for my commentary and feedback. I will add square brackets to describe something, e.g. [Optimization] might refer to a small optimization. You should keep a list of these commands, what they mean, and their common use cases."

- **Test example 3:** "Let's ensure our programming currently allows us to achieve this insight: agents should quickly understand the state of work when starting with a fresh context window. Let's analyze how well our 'loading from zero' works, and see if we can improve it."

---

## The Work Cycle

When you are completing large units of work, follow this cycle (this is not new, others have used this, and there are even agent frameworks around this like ReAct):

**Figure 3: The Work Cycle**

```
┌─────────────────────────────────────────────────────────────┐
│                     THE WORK CYCLE                           │
└─────────────────────────────────────────────────────────────┘

    ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
    │  INPUT   │────▶│   PLAN   │────▶│ EXECUTE  │────▶│  LEARN   │
    │          │     │          │     │          │     │          │
    │ Task +   │     │ Agent    │     │ Agent    │     │ Update   │
    │ Context  │     │ creates  │     │ performs │     │ memory,  │
    │          │     │ plan     │     │ actions  │     │ evolve   │
    └──────────┘     └──────────┘     └──────────┘     └──────────┘
         │                                                   │
         └───────────────────────────────────────────────────┘
                         (repeat for next task)
```

**1. Input** - Provide the task and context

**2. Plan** - Have the agent plan (Claude Code will automatically do this in plan mode)
- Review and provide feedback on the plan if you want more precision
- Otherwise just one-shot it
- This should ideally involve a reasoning step

**3. Execute / Act** - Have the agent execute the plan, or perform the planned action
- Execution can be: building code, refactoring, creating new workflows, optimizing itself, etc.
- Review and provide feedback on execution if you want more precision, otherwise just one-shot it and review the final product at the end
- Action can be: any non-execution based task you ask it to do on the computer or internet
- You can of course have a mixture of both

**4. Learn** - Have the agent run the `/cleanup` or `/evolve` command to:
- Update its memory (progress tracking, logs, todos, etc.)
- Maintain internal consistency
- Evolve its morphic code (should be conservative)
- Run any other cleanup tasks (create commit messages, running tests, committing, etc.)

Claude Code currently does not do this learning step well on its own, so you need custom morphic code for many of these steps.

---

# Part 5: Conclusion and Future Topics

## Parting Words

This was just a starting primer for what I'm seeing. I wanted to get this out fast so that people can start using these mental models and also build on them.

I definitely don't know a lot, and I don't pretend I do. But if we can all abstract a level or two up, and adopt some of the principles of morphic programming, we can really start to leverage the full capability of these models and agents while still maintaining confidence in the systems as they get more complex.

Underlying models will only get smarter, and this programming paradigm is designed to continue to get stronger and more leveraged as the unit of compute gets more intelligent.

---

## Future Topics

A few areas I'm thinking of exploring further in future entries. I would also love your feedback.

**More first principles** - I have many more that I haven't included for brevity.

**Cognitive architectures** - To orchestrate planning, execution, learning, and action. Memory is huge and under-developed in my implementation. Learning is also huge and I find it difficult to stabilize.

**Reinforcement learning in the real world** - What is the best loss function for self-improving agents?

**LifeOS** - Getting this to do everything that you could possibly want. My goal is to do this in a fully private way that is not reliant on closed-source models, as I don't really trust them with sensitive data.

**Self-improvement** - Getting agents to improve their own morphic programming. You need a clear, specific, and ideally business-relevant evaluation metric.

**Advanced agent orchestration** - Claude agents, Claude skills, MCPs, multi-agent orchestration.

**Advanced context engineering** - More sophisticated approaches to context management.

**Mirror of consciousness?** - What I'm ultimately interested in is whether we can design these AI systems in ways that can mirror our internal quality of experience. I don't think they will become conscious, but they can act as interesting mirrors for us to examine our own psyches, deep selves, or souls (whatever you might want to call it). If you are interested in this stuff, DM me :)

---

## Get in Touch

**This manual is free** - I don't need anything from you. If you gained value from it, please share with your friends or someone you care about.

**I'm working on more** - A more complete version of this manual (more principles, deeper discussion of advanced topics, more examples and morphic code). I'll also release a compressed version of the first principles and system design that you can add as system context in your own morphic system. Star or watch the repo as I might make updates or add new sections. If interested in early access or updates, DM or email me "MORPHIC".

**I want your feedback** - What worked? What didn't? What did I miss? What should I cover next?

**Connect with me:**
- LinkedIn: [https://www.linkedin.com/in/nicolasahar/](https://www.linkedin.com/in/nicolasahar/)
- Google Scholar: [https://scholar.google.com/citations?user=CEG32p4AAAAJ&hl=en](https://scholar.google.com/citations?user=CEG32p4AAAAJ&hl=en)
- GitHub: [https://github.com/nicolasahar](https://github.com/nicolasahar)
- X/Twitter: [https://x.com/SaharNicola](https://x.com/SaharNicola)

---

# Appendix: Generic Commands Reference

Here are the essential commands for any morphic programming system, categorized by purpose:

| Category | Command | Purpose | Key Steps |
|----------|---------|---------|-----------|
| **Priming** | `/prime-agent` | Load context for new session | Read core docs, load state, verify setup |
| **Priming** | `/rebuild` | Reconstruct system from specification | Read spec, create structure, initialize |
| **Maintenance** | `/cleanup` | Post-task consistency checks | Verify refs, sync docs, update progress |
| **Maintenance** | `/sync-docs` | Keep documentation in sync | Compare docs to reality, fix drift |
| **Improvement** | `/evolve` | Self-improvement from observations | Analyze patterns, propose changes, apply |
| **Improvement** | `/optimize` | Surgical targeted improvements | Find bottleneck, fix specifically |
| **Improvement** | `/refactor` | Reduce morphic complexity | Audit, consolidate, simplify |
| **Abstraction** | `/abstract` | Convert manual task to command | Review conversation, extract pattern, create command |
| **Testing** | `/test` | Run tests on changes | Execute test suite, report results |
| **Testing** | `/evaluate` | Test E2E autonomy capabilities | Run task suite, measure success rates |
| **Logging** | `/progress` | Log major milestones | Create detailed progress entry |
| **Logging** | `/log` | Save conversation for analysis | Capture conversation, extract patterns |

**Basic structure for any command:**

```markdown
# /command-name

## Description
One-line description of what this command does.

## Inputs
- Required input 1
- Optional input 2 (default: value)

## Workflow
1. Step one
2. Step two
3. Step three

## Output
What the command produces or reports.
```

---

*Written in December 2025. Last updated: December 31, 2025.*

*This manual was produced using the morphic programming system it describes. The outline, first principles, and core ideas are entirely human-generated. The polish, examples, and formatting were AI-assisted.*

---

# Licence

Copyright (c) 2025 Nicola Sahar

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
