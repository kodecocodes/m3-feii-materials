# Token Usage

This document outlines the approximate token usage in this module.

## Tools for Measuring Token Count

### Claude Agent in Xcode and Conductor

In Xcode 27, Xcode and Claude don't show the token count. Therefore, [**ccusage**](https://ccusage.com) calculated the tokens. The same tool was used for the Conductor sessions in Lesson 2, since Conductor is backed by the same Claude Agent SDK.

## Important Caveats Before Proceeding

Here are a few key points:

- The numbers reported here are approximate.
- Token counts can vary significantly depending on the model used.
- AI output can vary on every run.
- The second model row in a demo's totals (`sonnet-4-6`) represents tokens consumed by subagents — either subagents spawned within a Claude Agent conversation (Lesson 1), or Conductor's separate review pass over a reviewed branch (Lesson 2).
- Throughout this course, use `/usage` in an Xcode conversation with Claude Agent to learn more about your usage quota and costs.

## Token Usage for Claude Agent in Xcode

### Prepare the Plan for Execution

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 74 | 520,335 | 3,794,964 | 76,123 | |
|sonnet-4-6 | 57 | 127,581 | 1,561,909 | 12,191 | |
|**Total** | | | | | **~6,093,234** |

**Per-prompt breakdown**

*Prompt 1: Review the Plan for Gaps*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 12 | 89,767 | 390,433 | 5,901 | **~486,113** |

*Prompt 2: List the Open Questions*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 16 | 103,868 | 662,953 | 9,008 | **~775,845** |

*Prompt 3: Recommend Resolutions for Each Open Point*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 2 | 504 | 99,849 | 3,529 | **~103,884** |

*Prompt 4: Build the Execution Plan*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 4 | 13,054 | 204,346 | 9,601 | **~227,005** |

*Prompt 5: Document the Decisions in One Place*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 6 | 4,222 | 342,647 | 2,990 | **~349,865** |

*Prompt 6: Confirm the Open Points*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 14 | 4,642 | 838,418 | 2,848 | **~845,922** |

*Prompt 7: Start the Implementation Workflow*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 20 | 304,278 | 1,256,318 | 42,246 | |
|sonnet-4-6 | 57 | 127,581 | 1,561,909 | 12,191 | |
|**Total** | | | | | **~3,304,600** |

> Prompt 7 is where the agent spawned subagents to implement the execution plan in parallel — the `sonnet-4-6` row is the combined cost of every subagent it launched.

## Token Usage for Conductor

### Reviewing With Conductor

Conductor ran three parallel sessions, each auditing the implementation against a different part of `reviewed-feature-plan.md`, plus one separate review pass over the branch. Each session had a single prompt, so the per-session and per-prompt totals are the same.

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 208 | 906,254 | 12,667,445 | 77,814 | |
|sonnet-4-6 | 19 | 118,303 | 859,235 | 24,558 | |
|**Total** | | | | | **~14,653,836** |

*Session 1: Audit Against Goals and Non-Goals*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 42 | 383,873 | 2,154,644 | 21,119 | **~2,559,678** |

*Session 2: Audit Against the Proposed Swift Surface*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 84 | 251,291 | 5,470,012 | 33,862 | **~5,755,249** |

*Session 3: Audit Against Edge Cases and Acceptance Criteria*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 82 | 271,090 | 5,042,789 | 22,833 | **~5,336,794** |

*Review pass: Conductor's reviewer agent over Session 2's branch*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-4-6 | 19 | 118,303 | 859,235 | 24,558 | **~1,002,115** |

> Conductor is configured to automatically run a second-opinion review pass with `sonnet-4-6` over a session's branch. In this demo, that pass ran once, over Session 2's branch — it's the source of the `sonnet-4-6` row in the combined total above.

## Token Usage for Xcode's Specialist Agents

### Auditing With Xcode's Specialist Agents

Each specialist agent ran as its own single-prompt conversation.

*Prompt 1: Run the Dynamic Type Specialist*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 16 | 27,654 | 651,757 | 10,066 | **~689,493** |

*Prompt 2: Run the VoiceOver Specialist*

| Model | Input | Cache Create | Cache Read | Output | Total Tokens |
| ---: | ---: | ---: | ---: | ---: | ---: |
|sonnet-5 | 20 | 125,510 | 879,982 | 23,228 | **~1,028,740** |
